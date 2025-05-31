pipeline {
    agent any

    environment {
        DOCKER_HOST = 'unix:///var/run/docker.sock'
    }

    stages {
        stage('Construir contenedores') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Desplegar') {
            steps {
                sh '''
                    docker rm -f app_web || true
                    docker rm -f ci_jenkins || true
                    docker-compose down || true
                    docker-compose up -d
                '''
            }
        }
    }
}