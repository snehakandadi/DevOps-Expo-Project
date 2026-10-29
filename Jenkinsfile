pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the project from GitHub'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image'
                bat 'docker build -t devops-expo .'
            }
        }

        stage('Deploy Website') {
            steps {
                echo 'Deploying website using Docker'
                bat 'docker rm -f expo-website || exit /b 0'
                bat 'docker run -d -p 8081:80 --name expo-website devops-expo'
            }
        }
    }
}