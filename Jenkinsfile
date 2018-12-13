pipeline {
  agent {
    docker {
        image 'maven:3.6.0-jdk-8'
    }
  }
  triggers {
    cron '@midnight'
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '30', artifactNumToKeepStr: '5'))
  }
  stages {
    stage('build') {      
      steps {        
        script {
          maven cmd: 'clean install'
        }
      }
      post {
        success {
          archiveArtifacts 'xtrans/target/*.iar'
        }
      }
    }
  }
}