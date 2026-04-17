pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git credentialsId: 'jenkins-github-integrate', url:'https://github.com/pratikk-devops/devops-fastapi-test.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker compose build '
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker compose down || true'
                sh 'docker compose up -d'
            }
        }
        stage('Test Persistence') {
            steps {
                script {
                    // wait for the application to start
                    sh 'sleep 10'

                    // Call API to check the existing users
                    sh '''
                    curl -X GET http://localhost:8000/users
                    '''
                }
            }
        }
    }
}
