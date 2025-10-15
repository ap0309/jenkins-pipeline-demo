pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ap0309/jenkins-pipeline-demo.git'
            }
        }

         stage('Build') {
            steps {
                echo 'Installing dependencies...'
                bat '"C:\\Users\\ayush\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install --upgrade pip'
                bat '"C:\\Users\\ayush\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install -r requirements.txt'
                bat '"C:\\Users\\ayush\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install pytest'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat '"C:\\Users\\ayush\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pytest --junitxml=report.xml'
            }
        }
    }

    post {
        always {
            echo 'Publishing test results...'
            junit '/report.xml'
        }
    }
}
