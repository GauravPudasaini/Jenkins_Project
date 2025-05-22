pipeline {
    agent any

environment {
    IMAGE_NAME = 'gaurav123/my-first-image'   // Replace with your actual values
    CREDENTIALS_ID = 'dockerhub-creds'        // ID from Jenkins credentials
}

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/your-repo.git'  // Replace with your GitHub repo
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "${CREDENTIALS_ID}") {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
