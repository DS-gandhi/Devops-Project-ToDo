pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/DS-gandhi/Devops-Project-ToDo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t todo-app:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker stop todo-app || true'
                sh 'docker rm todo-app || true'
                sh 'docker run -d -p 5000:5000 --name todo-app todo-app:latest'
            }
        }
    }
}
