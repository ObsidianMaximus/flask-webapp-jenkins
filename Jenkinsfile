pipeline {
    agent {
        docker { image 'ubuntu:latest' }
    }

    environment {
        IMAGE_NAME = 'flask-webapp'
        IMAGE_TAG = 'latest'
        DOCKER_REGISTRY = 'https://registry.hub.docker.com'
    }

    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry("https://${DOCKER_REGISTRY}", 'docker-credentials-id') {
                        docker.image("${IMAGE_NAME}:${IMAGE_TAG}").push()
                    }
                }
            }
        }
    }
}