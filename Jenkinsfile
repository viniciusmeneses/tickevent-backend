pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '--> Instalando dependências do projeto'
        bat 'npm install'
        echo '--> Compilando projeto'
        bat 'npm run build'
      }
    }

    stage('Test') {
      steps {
        echo '--> Verificando problemas de sintaxe no código'
        bat 'npm run lint'
      }
    }

    stage('Deploy') {
      steps {
        input 'Realizar deploy no ambiente de produção?'
        bat 'git push heroku jenkins:master'
      }
    }

  }
  environment {
    PORT = '3000'
  }
}