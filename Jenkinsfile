pipeline {
    agent any

    environment {
        IMAGE_NAME = "chat-app"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/<your-username>/chat-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh '''
                    docker stop chat-app || true
                    docker rm chat-app || true
                    docker run -d -p 3000:3000 --name chat-app ${IMAGE_NAME}
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete'
        }
    }
}

