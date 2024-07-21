pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('karim-dockerhub')
        DOCKER_IMAGE = 'myapp/flask'
    }

    stages {
        stage('Login to DockerHub') {
            steps {
                    // Login to DockerHub
                    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                
            }
        }

        stage('Build Docker Image') {
            steps {
                    // Build the Docker image and tag it with the BUILD_NUMBER
                    sh 'docker build -t $DOCKER_IMAGE:$BUILD_NUMBER .'
            }
        }

        stage('Push Docker Image to DockerHub') {
            steps {
                    // Push the Docker image to DockerHub
                    sh 'docker push $DOCKER_IMAGE:$BUILD_NUMBER'
                
            }
        }
    }
}
