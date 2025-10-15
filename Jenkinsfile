﻿pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/princebhanderi/jenkins-pipeline-demo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                bat '"C:\\Users\\Prince Faldu\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install --upgrade pip'
                bat '"C:\\Users\\Prince Faldu\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install -r requirements.txt'
                bat '"C:\\Users\\Prince Faldu\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install pytest'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat '"C:\\Users\\Prince Faldu\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pytest --junitxml=report.xml'
            }
        }
    }

    post {
        always {
            echo 'Publishing test results...'
            junit '**/report.xml'
        }
    }
}
