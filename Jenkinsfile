pipeline {
    agent any

    environment {
        DOCKER_COMPOSE = "C:\Users\darsh\user-data-app\docker-compose.yml" // path to docker-compose
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kkdarshan/user_data_devops.git'
            }
        }

        stage('Build & Deploy') {
            steps {
                sh "${DOCKER_COMPOSE} down"
                sh "${DOCKER_COMPOSE} up -d --build"
            }
        }
    }

    post {
        success {
            echo "Deployment Successful!"
        }
        failure {
            echo "Deployment Failed!"
        }
    }
}
