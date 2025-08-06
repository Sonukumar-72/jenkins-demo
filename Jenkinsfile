pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo ' Checking out code...'
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                echo  'Building Docker image...'
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Test') {
            steps {
                echo ' Running Tests (skipped - static HTML app)'
            }
        }

        stage('Deploy') {
            steps {
                echo ' Deploying container...'
                sh 'docker rm -f jenkins-demo-container || true'
                sh 'docker run -d -p 8085:80 --name jenkins-demo-container jenkins-demo-app'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline Completed Successfully!'
        }
        failure {
            echo ' Pipeline Failed.'
        }
    }
}
