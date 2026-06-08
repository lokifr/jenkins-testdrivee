pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/lokifr/jenkins-testdrivee.git'
            }
        }


        stage('Test') {
            steps {
                echo "Testing application"
            }
        }


        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-app .'
            }
        }

    }
}