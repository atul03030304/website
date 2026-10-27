pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'atul03030304/intellipaat-website:v1'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/atul03030304/website.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKERHUB_USER',
                    passwordVariable: 'DOCKERHUB_TOKEN'
                )]) {
                    sh '''
                        echo "$DOCKERHUB_TOKEN" | docker login -u "$DOCKERHUB_USER" --password-stdin
                        docker push "$DOCKER_IMAGE"
                        docker logout
                    '''
                }
            }
        }
    }
}
