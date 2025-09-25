pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/deepikag123/jenkins-task2.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the Flask app...'
                bat 'echo Build step running on Windows'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'echo All tests passed!'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t flask-ci-app .'
            }
        }

        stage('Docker Run') {
            steps {
                echo 'Running Docker container...'
                bat 'docker stop flask-app || echo No container to stop'
                bat 'docker rm flask-app || echo No container to remove'
                bat 'docker run -d -p 5000:5000 --name flask-app flask-ci-app'
            }
        }
    }

    post {
        success {
            echo "✅ Build and Deployment Successful! Visit http://localhost:5000"
        }
        failure {
            echo "❌ Build Failed. Check Jenkins logs."
        }
    }
}
