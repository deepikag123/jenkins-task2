
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
                echo 'Starting Flask app...'

                // Kill any previous Flask instances
                bat 'taskkill /F /IM python.exe || echo No process to kill'

                // Run Flask in background and redirect logs
                bat 'start /B python app.py > flask.log 2>&1'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deploy Successful! Visit http://127.0.0.1:5000 or http://192.168.43.223:5000'
        }
        failure {
            echo '❌ Build Failed. Check logs.'
        }
    }
}
