#!groovy
pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
      stage('Checkout'){
        steps {
        checkout scm
        }
      }
      stage('Setup'){
        steps {
        sh 'npm config set registry http://registry.npmjs.org'
        sh 'npm install --save-dev'
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
