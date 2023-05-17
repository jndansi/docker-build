pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository from GitHub
                git 'https://github.com/jndansi/docker-build.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image using Dockerfile in your repository
                script {
                    docker.build('jndansi/new-fruit:latest', '.')
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                // Push the Docker image to a Docker registry (e.g., Docker Hub)
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        docker.image('jndansi/new-fruit:latest').push()
                    }
                }
            }
        }
    }
}







