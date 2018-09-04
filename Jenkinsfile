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
        bat 'mvn clean install'
      }
    }
    
    stage("Nexus"){
      steps {
        nexusPublisher nexusInstanceId: 'Nexus_3.13', nexusRepositoryId: 'MobileWeb', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'C:/Program Files (x86)/Jenkins/workspace/MobileWeb_Pipeline/target/MobileWebMaven.war']], mavenCoordinate: [artifactId: 'MobileWeb', groupId: 'com.ibm.services', packaging: 'war', version: '1.4-SNAPSHOT']]]
      }
    }
    
    stage("Sonarqube"){
      steps {
        withSonarQubeEnv('SonarQube_6.7.5') {
           bat 'mvn sonar:sonar'
        }
      }
    } 
  }
}
