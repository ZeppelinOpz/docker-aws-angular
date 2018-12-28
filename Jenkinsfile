pipeline {
    agent {
        docker { image 'node:7-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                checkout scm
                sh 'node --version'
                sh 'pwd'
                sh 'ls'
                sh 'docker-compose up --build'
            }
        }
    }
}