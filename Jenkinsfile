pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/jayuttam/retail-sales-forecasting.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t retail-forecast .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop retail-container || true'
                sh 'docker rm retail-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name retail-container -p 8501:8501 retail-forecast'
            }
        }
    }
}