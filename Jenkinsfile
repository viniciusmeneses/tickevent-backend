pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '--> Instalando depend�ncias do projeto'
        bat 'npm install'
        echo '--> Compilando projeto'
        bat 'npm run build'
      }
    }

    stage('Test') {
      steps {
        echo '--> Verificando problemas de sintaxe no c�digo'
        bat 'npm run lint'
      }
    }

    stage('Deploy') {
      steps {
        input 'Realizar deploy no ambiente de produ��o?'
        bat 'git push heroku jenkins:master'
      }
    }

  }
  environment {
    PORT = '3000'
  }
}