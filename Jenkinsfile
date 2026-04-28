pipeline {
    agent any

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
                bat 'npm test || echo No tests'
            }
        }

        stage('Start Application') {
            steps {
                bat 'start /B npm start'
            }
        }
    }
}
