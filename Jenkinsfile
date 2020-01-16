#!groovy
pipeline {
    agent any
    stages {
      stage('Checkout'){
        steps {
        checkout scm
        }
      }
      stage('Setup'){
        steps {
        sh 'npm config set registry http://registry.npmjs.org'
        sh 'npm install'
        }
      }

      stage('Test'){
        steps {
        sh './node_modules/mocha/bin/mocha'
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
