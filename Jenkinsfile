pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t demo-app:v1 .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f demo-container || true
                docker run -d --name demo-container -p 8090:80 demo-app:v1
                '''
            }
        }
    }
}
