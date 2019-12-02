pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '--> Instalando dependencias do projeto'
        bat(script: 'npm install --loglevel verbose', encoding: 'UTF-8')
        echo '--> Compilando projeto'
        bat(script: 'npm run build', encoding: 'UTF-8')
        sleep 5
      }
    }

    stage('Test') {
      steps {
        echo '--> Verificando problemas de sintaxe no codigo'
        bat 'npm run lint'
        sleep 5
      }
    }

    stage('Deploy') {
      steps {
        input 'Realizar deploy no ambiente de producao?'
        bat 'git push heroku jenkins:master'
      }
    }

  }
  environment {
    PORT = '3000'
  }
}