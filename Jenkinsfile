pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/MixedMachine/simple-signin-backend', branch: 'prod')
        sh 'go mod tidy'
      }
    }

    stage('Log') {
      parallel {
        stage('Log') {
          steps {
            sh 'ls -la'
            sh 'go version'
          }
        }

        stage('Unit tests') {
          steps {
            sh 'go test ./...'
          }
        }

      }
    }

  }
}