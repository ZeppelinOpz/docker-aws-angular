pipeline {
  agent { 
    docker { 
      image 'ugurkavcu/angular-aws:latest'
      args '--entrypoint=""'
    }
  }
  stages {
    stage('Build') {
      steps {
        withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
          sh 'sleep 2m'
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