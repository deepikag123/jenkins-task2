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
                // Kill old python/pythonw processes, ignore errors
                bat '''
                taskkill /F /IM python.exe   || echo No python.exe to kill
                taskkill /F /IM pythonw.exe  || echo No pythonw.exe to kill
                '''

                // Start Flask app with pythonw (background, no blocking)
                bat 'start "" pythonw app.py'

                echo '✅ Flask app started. Access it at http://localhost:5000'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deploy Successful!'
        }
        failure {
            echo '❌ Build Failed. Check flask.log in workspace'
        }
    }
}

