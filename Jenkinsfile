pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo Building Application'
                sh 'date'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running Tests'
                sh 'hostname'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo Deploying Application'
            }
        }
    }
}
