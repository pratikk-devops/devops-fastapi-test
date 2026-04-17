pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git url:'https://github.com/pratikk-devops/devops-fastapi-test.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker compose up --build -d'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker-compose down || true'
                sh 'docker-compose up -d'
            }
        }
    }
}
