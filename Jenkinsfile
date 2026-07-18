pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t notes-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop notes-app || true
                docker rm notes-app || true
                docker run -d -p 80:5000 --name notes-app notes-app
                '''
            }
        }
    }
}
