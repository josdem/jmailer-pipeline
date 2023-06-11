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
       /*
        steps {
          echo 'Starting Build Job'
          build job: 'jmailer-spring-boot'
          print "Result: ${currentBuild.result}"
          echo 'Done!'
        }
        */
        options {
          catchError(message: "Test failed", stageResult: 'UNSTABLE', buildResult: 'UNSTABLE')
        }
        stages {
          stage('Test 1') {
            echo 'test 1 succeeded'
          }
          stage('Test 2') {
            error 'test 2 failed'
          }
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
