pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/obasjoe-007/devops-mini-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("devops-app:${env.BUILD_1}")
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    sh 'docker stop devops-app || true'
                    sh 'docker rm devops-app || true'
                    sh 'docker run -d -p 3001:3000 --name devops-app devops-app:${env.BUILD_1}'
                }
            }
        }
    }
}

