pipeline {
    agent {
        docker {
            image 'docker:24.0.2-cli' // any Docker CLI image
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('chat-app')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 3000:3000 --name chat-app chat-app'
                }
            }
        }
    }
}

