pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Scan') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'

                    withSonarQubeEnv('SonarQube') {
                        sh """
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=my-app \
                        -Dsonar.sources=.
                        """
                    }
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dipak2303/my-app:v1 .'
            }
        }
    }
}

stage('Deploy Container') {
    steps {
        sh '''
        docker stop my-app || true
        docker rm my-app || true

        docker run -d \
        --name my-app \
        -p 80:80 \
        dipak2303/my-app:v1
        '''
    }
}
