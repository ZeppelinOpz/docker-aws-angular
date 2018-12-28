pipeline {
  agent { 
    docker { 
      image 'docker/compose:1.21.0'
      args '--entrypoint=""'
    }
  }
  stages {
    stage('Build') {
      steps {
        docker.withRegistry('', 'docker-hub') {
          sh 'docker-compose up --build'
          sh 'docker tag aws-angular:10 ugurkavcu/aws-angular:latest'
          sh 'docker tag aws-angular:10 ugurkavcu/aws-angular:10'
          sh 'docker push ugurkavcu/aws-angular:latest'
          sh 'docker push ugurkavcu/aws-angular:10'
        }
      }
    }
  }
}