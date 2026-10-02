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
                    // Forcefully purana container stop aur remove kar do
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" rm -f running-app || ver > nul"
                    
                    // Naya container chalao
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" run -d --name running-app -p 8080:8080 my-node-app:${env.BUILD_NUMBER}"
                }
            }
        }
    }
}