pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from the repository
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image and tag it as 'my-node-app'
                    dockerImage = docker.build('my-node-app')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop and remove any existing container with the same name
                    sh 'docker rm -f my-node-app-container || true'

                    // Run the Docker container on your local machine
                    sh 'docker run -d -p 3000:3000 --name my-node-app-container my-node-app'
                }
            }
        }
    }

    post {
        always {
            // Clean up the workspace after the build
            cleanWs()
        }
    }
}
