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
                    // Purana container hatao
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" rm -f running-app || ver > nul"
                    
                    // Port 8081 use karte hain taaki conflict na ho (Host: 8081 -> Container: 8080)
                    bat "\"C:\\Users\\GuestUser\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe\" run -d --name running-app -p 8081:8080 my-node-app:${env.BUILD_NUMBER}"
                }
            }
        }
    }
}