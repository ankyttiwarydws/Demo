pipeline {
  agent any
  stages {
    

    stage('Build') {
      steps {
        withMaven(globalMavenSettingsConfig: 'null', jdk: 'jdk', maven: 'maven', mavenSettingsConfig: 'null') {
          sh 'mvn clean package'
        }

      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build . -t ankittiwaridws/demo:0.1 '
      }
    }

    stage('DockerHub Push') {
      steps {
        withCredentials(bindings: [string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
          sh "docker login -u ankittiwaridws -p ${dockerhub}"
          sh 'docker push ankittiwaridws/demo:0.1'
        }

      }
    }

  }
}
