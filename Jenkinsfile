pipeline {
    agent any
    environment {
        BASE_URL  = credentials('BASE_URL')
        USERNAME  = credentials('USERNAME')
        PASSWORD  = credentials('PASSWORD')
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
            publishHTML([
                allowMissing: false,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'html-report',
                reportFiles: 'index.html',
                reportName: 'Playwright HTML Report'
            ])
            allure([
                includeProperties: false,
                jdk: '',
                reportBuildStatus: true,
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
