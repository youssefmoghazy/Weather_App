pipeline {
    agent any

    environment {
        IMAGE_NAME = "python-app-image"
        CONTAINER_NAME = "python-app-container"
    }

    stages {
        stage('Checkout Code') {
            steps {                 
                script {
                    git branch: 'main', credentialsId: '0120', url: 'git@github.com:youssefmoghazy/Weather_App.git'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d --name $CONTAINER_NAME -p 5000:5000 $IMAGE_NAME'
                }
            }
        }
    }

    post {
        always {
            script {
                sh 'docker ps -a | grep $CONTAINER_NAME'
            }
        }
    }
}
