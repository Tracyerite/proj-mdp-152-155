pipeline {
    agent any

    environment {
        GIT_CREDENTIALS = 'github-creds' // Add this in Jenkins > Credentials
        DOCKER_HUB_CREDENTIALS = 'newtoken'
        IMAGE_NAME = 'tracyedisemi/web-calculator'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'project-1',
                    credentialsId: "${GIT_CREDENTIALS}",
                    url: 'https://github.com/Tracyerite/proj-mdp-152-155.git'
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



