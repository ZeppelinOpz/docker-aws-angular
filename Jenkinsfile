pipeline {
    agent any      
    stages {
        stage('Checkout') {
            steps {
               checkout scm
            }
        }
        stage('Build') {
            steps {
               sh 'docker build . -t angular'

               withDockerRegistry([ credentialsId: "docker-hub", url: "" ]) {
                 sh 'docker-compose up --build'
                 sh 'docker tag aws-angular:10 ZeppelinOps/aws-angular:latest'
                 sh 'docker tag aws-angular:10 ZeppelinOps/aws-angular:10'
                 sh 'docker push ZeppelinOps/aws-angular:latest'
                 sh 'docker push ZeppelinOps/aws-angular:10'
               }
            }
        }
    }
}