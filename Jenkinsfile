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
          echo 'Stopping Jmailer'
          sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/remove-jmailer.sh"'
          echo 'Done!'
        }
      }
      stage ('Build Jmailer Job') {
        steps {
          echo 'Starting Build Job'
          build job: 'jmailer-spring-boot'
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
