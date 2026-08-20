pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/praveentamiz/my-devops-app.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-devops-app:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop my-app-container || true'
                sh 'docker rm my-app-container || true'
                sh 'docker run -d --name my-app-container -p 8081:80 my-devops-app:latest'
            }
        }
    }
}
