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

  }
}