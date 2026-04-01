pipeline {
    agent any

    environment {
        IMAGE_NAME = "tokamohsen2001/flask-app"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'master', url: 'https://github.com/TokaMohsenSaad/first-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:latest", ".")
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('', 'docker-hub-credentials') {
                        docker.image("${IMAGE_NAME}:latest").push()
                    }
                }
            }
        }
    }
}
