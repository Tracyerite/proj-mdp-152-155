
pipeline {
    agent any

    environment {
        IMAGE_NAME = "calculator-app"
        CONTAINER_NAME = "calculator"
    }

   stage('Clone Repo') {
    steps {
        git branch: 'project-1', url: 'https://github.com/Tracyerite/proj-mdp-152-155.git'
     }
  }

        stage('Build WAR') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'  
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
                sh 'docker run -d -p 8081:8080 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
