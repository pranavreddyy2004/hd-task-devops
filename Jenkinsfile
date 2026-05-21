pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'py -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat 'py -m pytest'
            }
        }

        stage('Code Quality') {
            steps {
                bat 'py -m flake8 app.py test_app.py'
            }
        }

        stage('Security') {
            steps {
                bat 'py -m bandit -r .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'echo Deploying Flask app to local test environment'
                bat 'start /B py app.py'
            }
        }

        stage('Release') {
            steps {
                bat 'echo Version 1.0 released successfully > release.txt'
            }
        }

        stage('Monitoring') {
            steps {
                bat 'powershell -Command "Start-Sleep -Seconds 5; Invoke-WebRequest http://127.0.0.1:5000/health"'
            }
        }
    }
}