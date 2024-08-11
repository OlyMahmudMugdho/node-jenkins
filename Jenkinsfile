pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('my-node-app')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    dockerImage.inside {
                        sh 'docker run -d -p 3000:3000 my-node-app'
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
