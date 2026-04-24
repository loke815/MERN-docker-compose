pipeline {
    agent any

    environment {
        DOCKER_USER = 'lokesh815'
        IMAGE_BACKEND = "${DOCKER_USER}/mern-backend"
        IMAGE_FRONTEND = "${DOCKER_USER}/mern-frontend"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/loke815/MERN-docker-compose.git'
            }
        }

        stage('Build Backend') {
            steps {
                dir('backend') {
                    sh 'docker build -t $IMAGE_BACKEND:$BUILD_NUMBER .'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh 'docker build -t $IMAGE_FRONTEND:$BUILD_NUMBER .'
                }
            }
        }

        stage('Push Images') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-creds') {
                        sh 'docker push $IMAGE_BACKEND:$BUILD_NUMBER'
                        sh 'docker push $IMAGE_FRONTEND:$BUILD_NUMBER'
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
