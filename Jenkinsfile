pipeline {
    agent any

    environment {
        IMAGE_NAME = "youssefmoghazy/python-app-image"
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
        stage('push image to docker hub'){
            steps{
                script{
                    sh 'docker push $IMAGE_NAME'
                }
            }
        }
        stage('list'){
            steps{
                script{
                    sh 'ls'
                }
            }
        }
        stage('Run ansible playbook'){
            steps{
                script{
                    sh 'export ANSIBLE_HOST_KEY_CHECKING=False'
                    sh 'chmod 600 ./privatefiles/private_key_m01'
                    sh 'chmod 600 ./privatefiles/private_key_m02'
                    sh 'ansible-playbook -i inventory playbook.yml'
                }
            }
        }
        
    }
    
    
}
