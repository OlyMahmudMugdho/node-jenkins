pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from the repository
                script {
                    sh 'git clone https://github.com/OlyMahmudMugdho/node-jenkins.git'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image and tag it as 'my-node-app'
                    sh 'cd node-jenkins && docker build -t my-nodejs-app .'
                }
            }
        }

        stage('Tag Docker Image') {
            steps {
                script {
                    // Build the Docker image and tag it as 'my-node-app'
                    sh 'docker tag my-nodejs-app olymahmudmugdho/my-nodejs-app'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Build the Docker image and tag it as 'my-node-app'
                    sh 'docker push olymahmudmugdho/my-nodejs-app'
                }
            }
        }



        // stage('Run Docker Container') {
        //     steps {
        //         script {
        //             // Stop and remove any existing container with the same name
        //             sh 'docker rm -f my-nodejs-app || true'

        //             // Run the Docker container on your local machine
        //             sh 'docker run -d -p 3000:3000 --name my-node-app-container my-nodejs-app'
        //         }
        //     }
        // }
    }

    post {
        always {
            // Clean up the workspace after the build
            cleanWs()
        }
    }
}
