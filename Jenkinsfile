pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t login-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker stop login-app || echo container not running
                docker rm login-app || echo container not found
                docker run -d -p 4000:4000 --name login-app login-app
                '''
            }
        }
    }
}
