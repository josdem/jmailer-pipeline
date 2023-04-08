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
   }
}
