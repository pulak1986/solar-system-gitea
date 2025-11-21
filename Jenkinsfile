pipeline {
    agent any
    
    tools {
        nodejs 'Node-JS-25.2.1'
    }

    stages {
        stage("Install Dependancies") {
            steps {
                sh 'npm install --no-audit'
           }
        }
        stage("npm Dependancy Audit") {
            steps {
                sh 'npm audit --audit-level=critical'
                echo $?
           }
        }
    }
}
