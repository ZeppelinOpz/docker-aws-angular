pipeline {
  agent { 
    docker { 
      image 'alpine:3.8'
      args '--entrypoint "/bin/sh"'
    }
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1') {
          sh 'docker-compose up --build'
          sh 'docker tag aws-angular:10 zeppelinops/aws-angular:latest'
          sh 'docker tag aws-angular:10 zeppelinops/aws-angular:10'
          sh 'docker push zeppelinops/aws-angular:latest'
          sh 'docker push zeppelinops/aws-angular:10'
        }
      }
    }
  }
}