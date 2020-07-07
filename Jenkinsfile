pipeline {
 agent any
 options {
  skipDefaultCheckout()
 }
 stages {
  stage('SCM') {
   steps {
    checkout scm
   }
  }
  stage('Build') {
    agent {
     docker {
      image 'node:latest'
      reuseNode true
      }
     }
     steps {
      sh 'npm install'
     }
   }
  stage('Unit Tests') {
   agent {
    docker {
     image 'node:latest'
     reuseNode true
    }
   }
   steps {
    node app.js &
    sh 'npm test'
   }
   post {
    always {
     junit 'target/surefire-reports/**/*.xml'
    }
   }   
  } 
 }
}