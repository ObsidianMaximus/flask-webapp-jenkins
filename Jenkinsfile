pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("obsidianmaximus/flask-webapp:latest")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry("https://registry.hub.docker.com/", 'docker-credentials-id') {
                        docker.image("obsidianmaximus/flask-webapp:latest").push()
                    }
                }
            }
        }
    }
}