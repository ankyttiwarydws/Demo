pipeline {
  agent any
  stages {
    stage('') {
      steps {
        git(url: 'https://github.com/ankyttiwarydws/Demo.git', branch: 'main', credentialsId: 'git', poll: true)
        sh 'sh "mvn clean package"'
        sh 'sh "docker build . -t ankittiwaridws/demo:${DOCKER_TAG}"'
      }
    }

  }
}