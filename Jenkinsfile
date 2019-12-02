pipeline {
  agent {
    node {
      label 'node'
    }

  }
  stages {
    stage('Build') {
      steps {
        echo '--> Installing project dependencies....'
        sh 'npm install'
      }
    }

  }
}