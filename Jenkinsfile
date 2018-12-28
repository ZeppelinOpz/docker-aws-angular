node {
    withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1') {    
      docker.image('docker/compose:1.21.0').withRun('--entrypoint /bin/sh') { c ->
        checkout scm        
        sh 'docker-compose up --build'
        sh 'docker tag aws-angular:10 zeppelinops/aws-angular:latest'
        sh 'docker tag aws-angular:10 zeppelinops/aws-angular:10'
        sh 'docker push zeppelinops/aws-angular:latest'
        sh 'docker push zeppelinops/aws-angular:10'
      }
    }
}