pipeline {
    agent any

    environment {
        IMAGE_NAME = 'deveshm026/stock-app'
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/tejaswinimoily35/StockTrackk.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS')]) {

                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }

        stage('Deploy using Ansible (LOCAL)') {
            steps {
                sh 'ansible-playbook -i hosts deploy.yml'
            }
        }
    }
}
