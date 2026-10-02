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
                bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" build -t my-node-app:${env.BUILD_NUMBER} ."
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" stop running-app || true"
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" rm running-app || true"
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" run -d --name running-app -p 8080:8080 my-node-app:${env.BUILD_NUMBER}"
                }
            }
        }
    }
}