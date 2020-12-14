pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            //args '-v /root/.m2:/root/.m2'
            args '-u root'
            //args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {

        stage('SCM Checkout') {
            steps {
                sh 'git clone https://github.com/ssrful/maven.java-fundamentals.git'
            }
        }
        stage('Compile-Package') {
            steps {
                script {
                    def mvnHome = tool name: 'maven-3', type: 'maven'
                    sh "${mvnHome}/bin/mvn/package"
                }
            }
        }

        stage('Maven Install') {
              agent {
                docker {
                  image 'maven:3.6.3'
                }
              }
              steps {
                sh 'mvn -Dmaven.test.failure.ignore=true'
              }
        }
    }
}