pipeline {
    agent {
        label 'devesh-slave-1'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/tejaswinimoily35/StockTrackk.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Build') {
            steps {
                bat 'echo Build stage complete - MongoDB env configured separately'
            }
        }
    }
    post {
        success { echo 'Build Successful!' }
        failure { echo 'Build Failed!' }
    }
}
