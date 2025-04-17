pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "dsnkumar121/app:1.01"  // Docker Hub image name
        CONTAINER_NAME = "app_container"
        PORT = "5000"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', credentialsId: 'c0f61b32-c289-4e75-b32f-335ed09b3649', url: 'https://github.com/DSNdinesh/app.git'
            }
        }

        stage('Build and Deploy Locally with Docker Compose') {
            steps {
                sh '''
                docker-compose down || true  # Stop any running containers
                docker-compose up -d --build  # Build and start new containers
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}
