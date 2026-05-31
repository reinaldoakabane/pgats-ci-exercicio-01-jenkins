pipeline {
    agent any

    options {
        timeout(time: 20, unit: 'MINUTES')
    }

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
                sh 'npx playwright install chromium'
            }
        }

        stage('E2E Tests') {
            steps {
                sh 'npx playwright test --reporter=line --workers=1'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado'
        }
    }
}