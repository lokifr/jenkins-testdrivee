pipeline {

    agent any

    tools {
        sonarScanner 'sonar-scanner'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/lokifr/jenkins-testdrivee.git'
            }
        }


        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=jenkins-test \
                    -Dsonar.sources=.
                    '''
                }
            }
        }


        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-app .'
            }
        }

    }
}