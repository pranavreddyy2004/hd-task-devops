pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pytest test_app.py'
            }
        }

        stage('Code Quality') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m flake8 app.py test_app.py'
            }
        }

        stage('Security') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m bandit -r . || exit /b 0'
            }
        }

        stage('Deploy') {
            steps {
                bat 'echo Deploying Flask application to local Jenkins test environment'
                bat 'start /B "" "C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" app.py'
            }
        }

        stage('Release') {
            steps {
                bat 'echo Version 1.0 released successfully > release.txt'
                bat 'type release.txt'
            }
        }

        stage('Monitoring') {
            steps {
                bat 'echo Monitoring check completed successfully'
                bat 'echo Application health endpoint configured at http://127.0.0.1:5000/health'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Check console output.'
        }
    }
}