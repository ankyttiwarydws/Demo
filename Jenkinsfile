pipeline {
  agent any
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
            steps{
                agent any
                sh 'docker build -t ankittiwaridws/demo:1 .'
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
