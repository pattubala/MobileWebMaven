pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage("build"){
      steps {
        sh 'mvn clean package'
      }
    }
    stage("Nexus"){
      steps {
        nexusPublisher nexusInstanceId: 'Nexus_3.23', nexusRepositoryId: 'MobileWeb', packages: []
      }
    }
  }
}
