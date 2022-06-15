pipeline {
  agent any
  environment {
imagename = "ank/dem"
dockerImage = ''
  }
  tools {
    maven 'maven'
    jdk    'jdk'
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('DockerBuilderPublisher'){
       script {
         dockerImage = docker.build imagename
        }   
        }
    stage('DockerHub Push'){
            steps{
                withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
                    sh 'docker login -u ankittiwaridws -p ${dockerhub}'
                    sh 'docker push ankittiwaridws/demo:1'
                }
            }
        }
  
}   
}
