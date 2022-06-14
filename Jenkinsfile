pipeline {
  agent any
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/ankyttiwarydws/Demo.git', branch: 'main', credentialsId: 'git')
      }
    }

    stage('Build') {
      steps {
        withMaven(globalMavenSettingsConfig: 'null', jdk: 'jdk', maven: 'maven', mavenSettingsConfig: 'null') {
          sh 'mvn clean package'
        }

      }
    }

    stage('Build Docker Image') {
      steps {
        sh "docker build . -t ankittiwaridws/demo:${DOCKER_TAG} "
      }
    }

    stage('DockerHub Push') {
      steps {
        withCredentials(bindings: [string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
          sh "docker login -u ankittiwaridws -p ${dockerhub}"
          sh "docker push ankittiwaridws/demo:${DOCKER_TAG}"
        }

      }
    }

  }
  environment {
    DOCKER_TAG = getDockerTag()
  }

}
 def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
     
 }
