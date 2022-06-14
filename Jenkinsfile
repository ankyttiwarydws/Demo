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
        sh 'mvn clean package'
      }
    }

  }
   stage('Build Docker Image'){
            steps{
                sh "docker build . -t ankittiwaridws/demo:1 "
            }
        }
        stage('DockerHub Push'){
            steps{
                withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
                    sh "docker login -u ankittiwaridws -p ${dockerhub}"
                    sh "docker push ankittiwaridws/demo:1"
                }
            }
        }
  tools {
    maven 'maven'
    jdk 'jdk'
    docker 'docker'
  }
}
