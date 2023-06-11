#!/usr/bin/env groovy
pipeline {
  agent any
    stages {
      stage('Stop Jmailer') {
        steps {
          echo 'Stopping Jmailer'
          sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/stop-jmailer.sh"'
          echo 'Done!'
        }
      }
      stage('Remove Jmailer') {
        steps {
          echo 'Removing Jmailer'
          sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/remove-jmailer.sh"'
          echo 'Done!'
        }
      }
      stage ('Build Jmailer Job') {
        steps {
          echo 'Starting Build Job'
          script {
            try {
              build job: 'jmailer-spring-boot'
            } catch (error){
              print "Jmailer build failed!"
              script {
                build job: 'jenkins-sandbox'
              }
              sh "exit 1"
            }
          }
          echo 'Done!'
        }
      }
      stage('Move Jmailer') {
        steps {
          echo 'Moving Jmailer'
          sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/move-jmailer.sh"'
          echo 'Done!'
        }
      }
      stage('Start Jmailer') {
        steps {
          echo 'Starting Jmailer'
          sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/start-jmailer.sh"'
          echo 'Done!'
        }
      }
   }
}
