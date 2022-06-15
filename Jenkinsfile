pipeline {
  agent any
  stages {
    stage('') {
      steps {
        git(url: 'https://github.com/ankyttiwarydws/nodejs-demo', branch: 'main', credentialsId: 'git')
      }
    }

  }
  tools {
    maven 'maven'
    jdk 'jdk'
    dockerTool 'docker'
  }
}