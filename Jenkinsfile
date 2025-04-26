pipeline {
    agent any

    environment {
        
        DOCKER_IMAGE = 'deepank123/my-nodejs-app'
        
       
        DOCKERHUB_CREDENTIALS = 'deb926e5-e1fb-45b0-9a7c-66004a98c694'
    }

    stages {
  
        stage('Clone repository') {
            steps {
         
                git branch: 'main', url: 'https://github.com/Deepankyadav1/deepank_jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
           
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

      
        stage('Push to Docker Hub') {
            steps {
                script {
                  
                    docker.withRegistry('https://index.docker.io/v1/', DOCKERHUB_CREDENTIALS) {
                       
                        docker.image(DOCKER_IMAGE).push('latest')
                    }
                }
            }
        }
    }
}

