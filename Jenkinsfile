pipeline {
    agent any
    environment {
        BACKEND_IMAGE  = "bambadra/docker-task-app_repo-backend"
        FRONTEND_IMAGE = "bambadra/docker-task-app_repo-frontend"
        VERSION = "${BUILD_NUMBER}"
    }
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Build Images') {
            steps {
                sh '''
                docker build -t $BACKEND_IMAGE:$VERSION ./backend
                docker build -t $FRONTEND_IMAGE:$VERSION ./frontend
                '''
            }
        }
        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }
        stage('Push Images') {
            steps {
                sh '''
                docker push $BACKEND_IMAGE:$VERSION
                docker push $FRONTEND_IMAGE:$VERSION
                '''
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                sudo kubectl set image deployment/backend backend=$BACKEND_IMAGE:$VERSION
                sudo kubectl set image deployment/frontend frontend=$FRONTEND_IMAGE:$VERSION
                '''
            }
        }
    }
}