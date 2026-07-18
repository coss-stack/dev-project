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
                sh 'docker build -t dev-project .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop dev-project || true
                docker rm dev-project || true
                docker run -d -p 80:5000 --name dev-project dev-project
                '''
            }
        }
    }
}
