pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'echo "--> Installing project dependencies"'
        bat 'npm install'
      }
    }

  }
}