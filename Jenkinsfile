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
      args '-v /var/jenkins_home/:/home/node'
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
     args '-v /var/jenkins_home/:/home/node'
     reuseNode true
    }
   }
   steps {
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