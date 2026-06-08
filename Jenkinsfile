pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/lokifr/jenkins-testdrivee.git'
            }
        }


        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner'

                    withSonarQubeEnv('sonarqube') {
                        sh """
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=jenkins-test \
                        -Dsonar.sources=.
                        """
                    }
                }
            }
        }


        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-app .'
            }
        }


        stage('Trivy Image Scan') {
            steps {
                sh 'trivy image python-app'
            }
        }

    }
}