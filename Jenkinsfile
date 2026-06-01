pipeline {
    agent {
        docker {
            image 'node:24'
        }
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Dependencies') {
            steps {
                sh 'yarn'
            }
        }

        stage('Playwright') {
            steps {
                sh 'npx playwright install --with-deps'
            }
        }

        stage('E2E') {
            steps {
                sh 'yarn run e2e'
            }
        }
    }
}