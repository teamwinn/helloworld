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
        sh 'sudo npm config set registry http://registry.npmjs.org'
        sh 'sudo npm install'
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
        sh 'sudo npm prune'
        sh 'rm node_modules -rf'
      }
    }
  }
}
