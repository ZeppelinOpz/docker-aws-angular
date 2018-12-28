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
        withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/users/zeppelinops') {
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