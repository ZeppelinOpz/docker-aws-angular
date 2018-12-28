pipeline {
  agent any
  stages {
    stage('Init') {
      steps {
        script {
          def GIT_COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
        }       
      }
    }
    stage('Build') {
      agent { 
        docker { 
          image 'docker/compose:1.21.0'
          args '--entrypoint=""'
        }
      }
      steps {
        withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {             
          sh 'docker-compose up --build'
          sh 'docker tag aws-angular:10 ugurkavcu/aws-angular:latest'
          sh 'docker tag aws-angular:10 ugurkavcu/aws-angular:10'
          sh 'docker push ugurkavcu/aws-angular:latest'
          sh 'docker push ugurkavcu/aws-angular:10'
          sh "echo ${GIT_COMMIT}"
        }
      }
    }
  }
}