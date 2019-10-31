pipeline {
  environment {
    registry = "dhfirststep/nodejs_firststep"
    registryCredential = 'doc_hub'
    dockerImage = ''
  }
  agent any
  stages {
    stage('clone repository') {
      steps {
        git 'https://github.com/Jeyakumargd/hw_nodejs.git'
      }
    }
    stage('Build docker image') {
      steps{
        script {
          dockerImage = docker.build registry + ":nodejspackage-$BUILD_NUMBER"
        }
      }
    }
    stage('Docker repo: Push image ') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          
          }
        }
      }
    }
       
  }
}

   
