pipeline {
    agent any

    environment {
        IMAGE_NAME = "chat-app"
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Docker Container') {
            steps {
                // Stop and remove any running container first
                sh '''
                docker stop $IMAGE_NAME || true
                docker rm $IMAGE_NAME || true
                docker run -d --name $IMAGE_NAME -p 3000:3000 $IMAGE_NAME
                '''
            }
        }
    }
}

