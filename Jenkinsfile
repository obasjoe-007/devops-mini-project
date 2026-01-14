pipeline {
    agent any

    environment {
        TAG = "latest"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app:${TAG} .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop devops-app || true
                docker rm devops-app || true
                docker run -d --name devops-app -p 8081:8080 devops-app:${TAG}
                '''
            }
        }
    }
}

