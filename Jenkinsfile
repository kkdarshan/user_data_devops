pipeline {
    agent { label 'windows' } // your Windows node label

    environment {
        DOCKER_COMPOSE = "C:/Users/darsh/user-data-app/docker-compose.yml"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kkdarshan/user_data_devops.git'
            }
        }

        stage('Build & Deploy') {
            steps {
                bat "docker-compose -f ${DOCKER_COMPOSE} down"
                bat "docker-compose -f ${DOCKER_COMPOSE} up -d --build"
            }
        }
    }

    post {
        success { echo "Deployment Successful!" }
        failure { echo "Deployment Failed!" }
    }
}
