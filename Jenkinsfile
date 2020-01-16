#!groovy
pipeline {
    agent { docker { image 'node' } }
    stages {
      stage('Checkout'){
        steps {
        checkout scm
        }
      }
      stage('Setup'){
        steps {
        sh 'npm install'
        }
      }

      stage('Test'){
        steps {
        sh './node_modules/mocha/bin/mocha --exit'
        }
      }

      stage('Cleanup'){
        steps {
        echo 'prune and cleanup'
        sh 'npm prune'
        sh 'rm node_modules -rf'
      }
    }
  }
}
