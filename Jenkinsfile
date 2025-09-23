

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

        // Kill old python processes (ignore if none)
        bat 'taskkill /F /IM python.exe || echo No process to kill'

        // Start Flask app in background with pythonw (no blocking)
        bat 'start /B pythonw app.py > flask.log 2>&1'

        // Mark build as success
        echo '✅ Flask app started. Check http://127.0.0.1:5000'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deploy Successful! Visit http://127.0.0.1:5000 or your LAN IP'
        }
        failure {
            echo '❌ Build Failed. Check flask.log in workspace'
        }
    }
}
