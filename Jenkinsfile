pipeline {
    agent {
        docker { image 'docker/compose:1.21.0' }
    }
    stages {
        stage('Test') {
            steps {                
                sh 'pwd'
                sh 'ls'
                sh 'docker-compose up --build'
            }
        }
    }
}