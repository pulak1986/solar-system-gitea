pipeline {
    agent any
    
    tools {
        nodejs 'Node-JS-25.2.1'
    }

    stages {
        stage("Check Node and NPM Version") {
            steps {
                sh 'npm install --no-audit"
           }
        }
    }
}
