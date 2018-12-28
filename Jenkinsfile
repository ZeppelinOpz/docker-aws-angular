pipeline {
 agent {
        docker { 
          image 'docker/compose:1.21.0'
          args  '--entrypoint /bin/sh'
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
          sh 'docker-compose up --build'
          sh 'docker tag aws-angular:10 zeppelinops/aws-angular:latest'
          sh 'docker tag aws-angular:10 zeppelinops/aws-angular:10'       
      }
    }
  }
}