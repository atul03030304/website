groovy
pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/atul03030304/website.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t intellipaat-website:v1 .'
            }
        }

        stage('Verify Docker Image') {
            steps {
                sh 'docker images intellipaat-website'
            }
        }
    }
}
