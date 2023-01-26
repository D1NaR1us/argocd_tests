pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '2'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('DockerHUB')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t d1nar1us/mynginx-fromjenkins .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push d1nar1us/mynginx-fromjenkins'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}