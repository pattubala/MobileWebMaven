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
        sh 'mvn clean install'
      }
    }
    stage("Nexus"){
      steps {
        nexusPublisher nexusInstanceId: 'Nexus_3.23', nexusRepositoryId: 'MobileWeb', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '/root/.jenkins/workspace/Pipeline-Sample/target/MobileWebMaven.war']], mavenCoordinate: [artifactId: 'MobileWeb', groupId: 'com.ibm.services', packaging: 'war', version: '1.0-SNAPSHOT']]]
      }
    }
  }
}
