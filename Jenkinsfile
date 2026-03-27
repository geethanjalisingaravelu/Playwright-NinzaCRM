pipeline {
    agent any

    environment {
        BASE_URL  = credentials('BASE_URL')   // Secret Text ID
        USERNAME  = credentials('USERNAME')   // Secret Text ID
        PASSWORD  = credentials('PASSWORD')   // Secret Text ID
    }

    stages {
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
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
