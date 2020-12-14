pipeline {
  agent {
        docker {
            image 'maven:3-alpine'
            args '-u root'
            //'-v /root/.m2:/root/.m2'
        }
  }
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
         sh "${mvnHome}/bin/mvn package -Dmaven.test.failure.ignore=true"
         }
      }
    }
  }
  post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
} 