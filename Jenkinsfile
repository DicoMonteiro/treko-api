pipeline {
    agent {
        docker { 
            image "node:8-alpine" 
            args "--network=skynet"
        }
    }
    stages {
        stage('Build') {
            steps {
                sh "npm install"
            }
        }
        
        stage('Test') {
            steps {
                sh "npm run test:ci"
            }
        }
    }

}
