pipeline {
    agent any

    environment {
        DOCKER_HUB_USERNAME = 'deepank123'
        DOCKER_HUB_REPO = 'deepank123/my-nodejs-app'
        DOCKER_CREDENTIALS_ID = 'deb926e5-e1fb-45b0-9a7c-66004a98c694'
    }

    stages {
        stage('Clone GitHub Repository') {
            steps {
                git url: 'https://github.com/Deepankyadav1/deepank_jenkins.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_HUB_REPO .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: "$DOCKER_CREDENTIALS_ID", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo $PASSWORD | docker login -u $USERNAME --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_HUB_REPO'
            }
        }
    }
}
