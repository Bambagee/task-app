pipeline {
    agent any

    stages {

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Verify Node') {
            steps {
                sh 'node -v'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t task-app .'
            }
        }

    }
}