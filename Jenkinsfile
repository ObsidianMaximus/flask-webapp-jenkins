pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("flask-webapp:latest")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry("https://registry.hub.docker.com", 'docker-credentials-id') {
                        docker.image("flask-webapp:latest").push()
                    }
                }
            }
        }
    }
}