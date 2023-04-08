#!/usr/bin/env groovy
pipeline {
  agent any
    stages {
      stage('Stop Jmailer') {
        steps {
          echo 'Stopping Jmailer'
          sh 'sudo systemctl status jmailer'
          echo 'Done!'
        }
      }
   }
}
