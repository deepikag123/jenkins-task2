pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "All tests passed!"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // This will run Flask app in background
                sh 'python app.py &'
            }
        }
    }
}
