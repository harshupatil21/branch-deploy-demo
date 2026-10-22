
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                sh 'git log -1 --oneline'
            }
        }

        stage('Build') {
            steps {
                sh 'ls -la'
                sh 'test -f index.html'
            }
        }

        stage('Test') {
            steps {
                sh 'test -s index.html'
                echo 'Testing website checks passed!'
            }
        }

        stage('Deploy Testing') {
            steps {
                sh 'cp index.html /var/www/branch-deploy/testing/'
                echo 'Testing deployment completed!'
            }
        }
    }

    post {
        success {
            echo 'Testing pipeline succeeded!'
        }
        failure {
            echo 'Testing pipeline failed!'
        }
    }
}
