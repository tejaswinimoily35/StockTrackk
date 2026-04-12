pipeline {
    agent any

    environment {
        IMAGE_NAME = 'deveshm026/stock-app'
    }

    stages {

        stage('Clone Code') {
    steps {
        git branch: 'main', url: 'https://github.com/tejaswinimoily35/StockTrackk.git'
    }
}

        stage('Build Docker Image') {
    steps {
        withCredentials([string(credentialsId: 'mongo-uri', variable: 'MONGODB_URI')]) {
            sh 'docker build --build-arg MONGODB_URI=$MONGODB_URI -t $IMAGE_NAME .'
        }
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
