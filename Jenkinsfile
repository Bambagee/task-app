pipeline {
    agent any
    stages {
        stage('Install Dependencies') {
            steps {
                dir('backend') {
                    sh 'npm install'
                }
            }
        }
        stage('Verify Environment') {
            steps {
                dir('backend') {
                    sh 'node -v'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                dir('backend') {
                    sh 'docker build -t task-app .'
                }
            }
        }
    }
}