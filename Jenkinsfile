pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Dependencies') {
            steps {
                sh 'npm install --legacy-peer-deps'
            }
        }

        stage('Playwright Install') {
            steps {
                sh 'npx playwright install'
            }
        }

        stage('E2E Tests') {
            steps {
                sh 'npx playwright test'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado'
        }

        success {
            echo 'Pipeline executado com sucesso 🚀'
        }

        failure {
            echo 'Pipeline falhou ❌'
        }
    }
}