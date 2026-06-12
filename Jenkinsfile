pipeline {
    agent any 

    stages {
        
        stage('Preparation') {
            steps {
                echo 'Preparing environment...'
                sh 'apt-get update && apt-get install -y python3'
            }
        }

        stage('Checkout') {
            steps {
                echo 'Fetching code from GitHub...'
                checkout scm
            }
        }

        stage('Test (CI)') {
            steps {
                echo 'Running Unit Tests...'
                sh 'python3 test_app.py'
            }
        }

        stage('Deploy (CD)') {
            steps {
                echo 'Deploying the application...'
                sh 'python3 app.py'
            }
        }
    }
    
    post {
        success {
            echo '🎉 Pipeline finished successfully!'
        }
        failure {
            echo '❌ Pipeline failed! Please check the logs.'
        }
    }
}