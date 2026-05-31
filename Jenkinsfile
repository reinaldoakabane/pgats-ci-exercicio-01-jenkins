pipeline {
    agent any

    options {
        timeout(time: 20, unit: 'MINUTES')
    }

    environment {
        CI = 'true'
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
                sh 'npx playwright install chromium --with-deps=false'
            }
        }

        stage('E2E Tests') {
            steps {
                sh 'npx playwright test --reporter=line --workers=1 --project=chromium'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado'
        }
    }
}