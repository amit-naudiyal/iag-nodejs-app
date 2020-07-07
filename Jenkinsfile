pipeline {
 agent any
 environment {
 }
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
      image 'node:6.14.4'
      args '-v /var/jenkins_home/:/home/node'
       // to use the same node and workdir defined on top-level pipeline for all docker agents
       reuseNode true
      }
     }
     steps {
      cd /home/node && sh 'npm install'
     }
   }
  stage('Unit Tests') {
   when {
    anyOf { branch 'master'; branch 'develop' }
   }
   agent {
    docker {
     image 'node:6.14.4'
     args '-v /root/.m2/repository:/root/.m2/repository'
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