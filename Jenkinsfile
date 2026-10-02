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
                script {
                    appImage = docker.build("my-node-app:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh "docker stop running-app || true"
                    sh "docker rm running-app || true"
                    appImage.run("-d --name running-app -p 8080:8080")
                }
            }
        }
    }
}