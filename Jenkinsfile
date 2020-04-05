pipeline {
  environment {
    registry = "basheer1993/basheer-docker"
    registryCredential = 'DockerCredentials'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Basheer1993/docker.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        
        }
      }
    }
    stage('Deploy Image') {
  steps{    script {
      docker.withRegistry( '', registryCredential ) {
        dockerImage.push()
      }
    }
  }
}
  }
}
