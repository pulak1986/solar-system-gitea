pipeline {
    agent any
    
    tools {
        nodejs 'Node-JS-25.2.1'
    }

    stages {

        stage("Install Dependencies") {
            steps {
                sh 'npm install --no-audit'
            }
        }

        stage('Dependency Scanning') {
            parallel {

                stage("npm Dependency Audit") {
                    steps {
                        sh 'npm audit --audit-level=critical || true'
                    }
                }

                stage("OWASP Dependency Check") {
                    steps {
                        sh 'mkdir -p odc-report'
                        dependencyCheck additionalArguments: '''
                            --scan .
                            --out odc-report
                            --format ALL
                            --prettyPrint
                        ''',
                        odcInstallation: 'dependancy-check-12.1.9'
                    }
                }

            }
        }
    }

    post {
        always {
            dependencyCheckPublisher pattern: 'odc-report/dependency-check-report.xml'
        }
    }
}

