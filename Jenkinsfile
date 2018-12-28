pipeline {
 agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      agent {
        docker { 
          image 'docker/compose:1.21.0'        
       }
      }
      steps {       
          sh 'docker-compose up --build'
          sh 'docker tag aws-angular:10 zeppelinops/aws-angular:latest'
          sh 'docker tag aws-angular:10 zeppelinops/aws-angular:10'       
      }
    }
  }
}