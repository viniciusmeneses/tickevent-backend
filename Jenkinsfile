pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '--> Instalando dependencias do projeto'
        bat(script: 'npm install --loglevel verbose', encoding: 'UTF-8')
        echo '--> Compilando projeto'
        bat(script: 'npm run build', encoding: 'UTF-8')
      }
    }

    stage('Test') {
      steps {
        echo '--> Verificando problemas de sintaxe no codigo'
        bat 'npm run lint'
      }
    }

    stage('Deploy') {
      steps {
        input 'Realizar deploy no ambiente de producao?'
        withCredentials([usernamePassword(credentialsId: '62e48e1a-7ce2-4426-bcfc-5e4904ff7723', passwordVariable: 'HEROKU_PASSWORD', usernameVariable: 'HEROKU_LOGIN')]) {
          bat 'git push https://%HEROKU_LOGIN%:%HEROKU_PASSWORD%@git.heroku.com/tickevent-backend.git HEAD:master -f'
        }
      }
    }

  }
  environment {
    PORT = '3000'
  }
}