pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/omkar701/login_form.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t login-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop login-app || true
                docker rm login-app || true
                docker run -d -p 5000:5000 --name login-app login-app
                '''
            }
        }
    }
}
