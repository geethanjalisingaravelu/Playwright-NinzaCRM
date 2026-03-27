pipeline {
    agent any

        environment {
        BASE_URL = credentials('BASE_URL')   // BASE_URL is Jenkins Secret Text ID
        USERNAME = credentials('USERNAME')   // USERNAME Secret Text ID
        PASSWORD = credentials('PASSWORD')   // PASSWORD Secret Text ID
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
