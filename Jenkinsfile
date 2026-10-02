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
                    // Windows ke liye 'ver > nul' use kiya hai error ignore karne ke liye
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" stop running-app || ver > nul"
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" rm running-app || ver > nul"
                    
                    // Naya container chalao
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" run -d --name running-app -p 8080:8080 my-node-app:${env.BUILD_NUMBER}"
                }
            }
        }
    }
}