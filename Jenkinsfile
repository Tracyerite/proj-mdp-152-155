pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = 'Docker-hub'
        IMAGE_NAME = 'tracyedisemi/web-calculator'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'project-1', url: 'https://github.com/Tracyerite/project1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "${DOCKER_HUB_CREDENTIALS}") {
                        docker.image("${IMAGE_NAME}:latest").push()
                    }
                }
            }
        }
    }
}
