pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        ## checkout scm
        sh 'make' 
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
      }
    }
  }
}
