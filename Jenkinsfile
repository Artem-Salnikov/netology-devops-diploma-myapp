#!groovy

pipeline {
	agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Docker Build') {
    	agent any
      steps {
      	sh 'docker build -t "artemsalnikov/myapp-nginx:$BUILD_NUMBER" .'
      }
    }
   stage('Dockerhub login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Docker push') {
      steps {
        sh 'docker push artemsalnikov/myapp-nginx:$BUILD_NUMBER'
      }
    }
  }
 }
