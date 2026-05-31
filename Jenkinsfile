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
                sh 'npm install -g yarn'
                sh 'yarn'
            }
        }

        stage('Playwright') {
            steps {
                sh 'yarn playwright install'
            }
        }

        stage('E2E') {
            steps {
                sh 'yarn run e2e'
            }
        }
    }
}