pipeline {
    agent any
    environment {
        IMAGE_NAME = 'bambadra/docker-task-app_repo'
        IMAGE_TAG = "${BUILD_NUMBER}"
    }
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
                sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_TOKEN'
                )]) {
                    sh 'echo $DOCKER_TOKEN | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker push ${IMAGE_NAME}:${IMAGE_TAG}'
                sh 'docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${IMAGE_NAME}:latest'
                sh 'docker push ${IMAGE_NAME}:latest'
            }
        }
        stage('Cleanup') {
            steps {
                sh 'docker logout'
                sh 'docker rmi ${IMAGE_NAME}:${IMAGE_TAG}'
                sh 'docker rmi ${IMAGE_NAME}:latest'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully - Image pushed to Docker Hub!'
        }
        failure {
            echo 'Pipeline failed - check the logs for details!'
        }
    }
}