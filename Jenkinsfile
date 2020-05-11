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
                sh "RUN echo 'http://dl-cdn.alpinelinux.org/alpine/v3.6/main' >> /etc/apk/repositories"
                sh "RUN echo 'http://dl-cdn.alpinelinux.org/alpine/v3.6/community' >> /etc/apk/repositories"
                sh "RUN apk update"
                sh "RUN apk add mongodb=3.4.4-r0"
                sh "apk add --no-cache mongodb"
                sh "chmod +x ./scripts/dropdb.sh"
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
