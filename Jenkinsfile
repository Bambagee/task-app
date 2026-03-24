pipeline {
agent any

environment {
    DOCKER_USERNAME = "bambadra"
    IMAGE_NAME = "docker-task-app_repo"
    TAG = "v1"
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
            sh 'docker build -t task-app .'
        }
    }

    stage('Tag Image') {
        steps {
            sh 'docker tag task-app $DOCKER_USERNAME/$IMAGE_NAME:$TAG'
        }
    }

    stage('Push Image') {
        steps {
            sh 'docker push $DOCKER_USERNAME/$IMAGE_NAME:$TAG'
        }
    }
}
```

}
