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

        stage('Playwright') {
            steps {
                sh 'npx playwright install --with-deps'
            }
        }

        stage('E2E') {
            steps {
                sh 'npx playwright test'
            }
        }
    }
}