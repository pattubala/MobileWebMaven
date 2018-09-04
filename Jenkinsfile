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
        nexusPublisher nexusInstanceId: 'Nexus_3.23', nexusRepositoryId: 'MobileWeb', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '/root/.jenkins/workspace/Pipeline-Sample/target/MobileWebMaven.war']], mavenCoordinate: [artifactId: 'MobileWeb', groupId: 'com.ibm.services', packaging: 'war', version: '1.3-SNAPSHOT']]]
      }
    }
    
    stage("Sonarqube"){
      steps {
        withSonarQubeEnv('SonarQube_6.7.5') {
           bat 'mvn sonar:sonar'
        }
      }
    } 
    stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
    }
  }
}
