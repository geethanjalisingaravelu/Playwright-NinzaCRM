pipeline {
    agent any

    environment {
        BASE_URL = "${{BASE_URL}}"
        USERNAME = "${{USERNAME}}"
        PASSWORD = "${{PASSWORD}}"
    }

    stages {
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }

 

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm run test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
