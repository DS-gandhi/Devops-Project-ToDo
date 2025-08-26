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
                bat 'docker build -t todo-app:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                // Stop old container if exists
                bat 'docker stop todo-app || exit 0'
                // Remove old container if exists
                bat 'docker rm todo-app || exit 0'
                // Run new container
                bat 'docker run -d -p 5000:5000 --name todo-app todo-app:latest'
            }
        }
    }
}
