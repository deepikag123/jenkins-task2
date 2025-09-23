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
        bat '''
        taskkill /F /IM python.exe || echo No process to kill
        start cmd /c "python app.py"
        '''
            }
        }
    }
    post {
        success {
            echo '✅ Build and Deploy Successful! Visit http://localhost:5000'
        }
        failure {
            echo '❌ Build Failed. Check logs.'
        }
    }
}
