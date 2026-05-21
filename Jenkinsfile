pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Launcher\\py.exe" -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Launcher\\py.exe" -m pytest test_app.py'
            }
        }

        stage('Code Quality') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Launcher\\py.exe" -m flake8 app.py test_app.py'
            }
        }

        stage('Security') {
            steps {
                bat '"C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Launcher\\py.exe" -m bandit -r .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'echo Deploying Flask app locally'
                bat 'start /B "C:\\Users\\dubba\\AppData\\Local\\Programs\\Python\\Launcher\\py.exe" app.py'
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