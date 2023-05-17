pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository from GitHub
                git 'https://github.com/jndansi/docker-build.git'
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build the Docker image using the Dockerfile in the repository
                    def dockerImage = docker.build('jndansi/new-fruit')

                    // Push the Docker image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
