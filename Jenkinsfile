pipeline {
    agent any

    environment {
        IMAGE_NAME = 'sample-web-app-test'
        DOCKERFILE = 'Dockerfile.dev'
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}", "-f ${DOCKERFILE} .")
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    docker.image("${IMAGE_NAME}").inside("-e CI=true") {
                        sh 'npm run test'
                    }
                }
            }
        }
    }
}
