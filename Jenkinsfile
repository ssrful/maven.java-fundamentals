pipeline {
  agent any
  stages {
  stage('Stage 1') {
      steps {
        script {
          echo 'Stage 1'
        }
      }
      }
  stage('Compile Package') {
      steps {
        script {
         echo 'Compile Package'
         def mvnHome = tool name: 'maven3.6.3', type: 'maven'
         sh "${mvnHome}/bin/mvn"
          }
      }
    }
  }
  post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
} 