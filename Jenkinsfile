pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      def GIT_COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
      steps {
        withDockerRegistry(credentialsId: 'docker-hub', url: 'http://hub.docker.com/u/zeppelinops') {
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