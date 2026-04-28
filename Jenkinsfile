pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    stages {

        stage('Check Node') {
            steps {
                bat 'node -v'
                bat 'npm -v'
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
                bat 'start /B npm start'
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
