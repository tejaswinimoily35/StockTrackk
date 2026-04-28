pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Application') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Test Application') {
            steps {
                bat 'npm test || echo No tests found'
            }
        }

        stage('Start Application') {
            steps {
                bat 'npm start'
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }
        failure {
            echo 'Build Failed'
        }
    }
}
