pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t html-app .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag html-app yourdockerhubusername/html-app:latest'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push yourdockerhubusername/html-app:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully 🚀'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}