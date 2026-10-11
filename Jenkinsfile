pipeline {
    agent any
    environment {
        IMAGE_NAME = 'dimasarya30/simple-app'
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Melakukan checkout dari SCM...'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Mulai build aplikasi'
                bat 'echo "Build selesai ✅"'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat "docker build -t ${IMAGE_NAME}:${env.BUILD_NUMBER} -t ${IMAGE_NAME}:latest ."
            }
        }
        stage('Push Docker Image') {
            steps {
                bat "docker push ${IMAGE_NAME}:${env.BUILD_NUMBER}"
                bat "docker push ${IMAGE_NAME}:latest"
            }
        }
    }
    post {
        always {
            echo 'Selesai build 🏁'
        }
    }
}