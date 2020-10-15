#!/usr/bin/env groovy

import java.text.SimpleDateFormat

pipeline {
  agent { node { label 'nodejs' } }
  options { timeout(time: 20, unit: 'MINUTES') }
  stages {
    stage('raw') {
      steps {
        script {
          node('maven.latest') {
            git url: 'https://github.com/akram/pipes.git'
            sh '''
               git clone https://github.com/akram/pipes.git
               cd pipes
               mvn clean package -X
               sleep 30
               '''
            }
          }
        script {
          node('nodejs') {
             git url: 'https://github.com/akram/nodejs-ex.git'
             sh '''
                git clone https://github.com/akram/nodejs-ex.git
                npm install
	        '''
          }
        }
      }
    }
  }
}


