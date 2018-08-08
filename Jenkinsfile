pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        sh 'make' 
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
      }
    }
  }
}
