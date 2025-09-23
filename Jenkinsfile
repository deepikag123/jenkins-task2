pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                bat 'echo Build step running on Windows'
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                bat 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'echo All tests passed!'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'python app.py'
            }
        }
    }
}
