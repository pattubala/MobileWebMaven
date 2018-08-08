pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        bat 'make' 
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
      }
    }
  }
}
