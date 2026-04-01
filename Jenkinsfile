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
        always {
            // HTML Report
            publishHTML([
                allowMissing: false,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'html-report',
                reportFiles: 'index.html',
                reportName: 'Playwright HTML Report'
            ])

            // Allure Report
            allure([
                includeProperties: false,
                jdk: '',
                results: [[path: 'allure-results']]
            ])
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
