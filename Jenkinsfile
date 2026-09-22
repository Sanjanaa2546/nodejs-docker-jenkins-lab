pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sanjanaa2546/nodejs-docker-jenkins-lab.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t nodejs-status-api .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker stop nodejs-status-container || exit 0'
                bat 'docker rm nodejs-status-container || exit 0'
                bat 'docker run -d -p 3000:3000 --name nodejs-status-container nodejs-status-api'
            }
        }
    }
}