pipeline {
    agent any

    environment {
        DOCKER_COMPOSE = "/var/lib/jenkins/user-data-app/docker-compose.yml"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kkdarshan/user_data_devops.git'
            }
        }

        stage('Build & Deploy') {
            steps {
                sh "docker-compose -f ${DOCKER_COMPOSE} down"
                sh "docker-compose -f ${DOCKER_COMPOSE} up -d --build"
            }
        }
    }

    post {
        success { echo "Deployment Successful!" }
        failure { echo "Deployment Failed!" }
    }
}
