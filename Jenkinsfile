pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/fullstack-app.git'
            }
        }

        stage('Build Frontend') {
            steps {
                sh 'docker build -t frontend ./frontend'
            }
        }

        stage('Build Backend') {
            steps {
                sh 'docker build -t backend ./backend'
            }
        }

        stage('Verify Build') {
            steps {
                sh 'docker images'
            }
        }

        stage('Deploy Database') {
            steps {
                sh 'docker compose up -d database'
            }
        }

        stage('Deploy Backend') {
            steps {
                sh 'docker compose up -d backend'
            }
        }

        stage('Deploy Frontend') {
            steps {
                sh 'docker compose up -d frontend'
            }
        }
    }

    post {

        success {
            echo 'Deployment Successful'
        }

        failure {
            echo 'Deployment Failed'
        }

    }
}
