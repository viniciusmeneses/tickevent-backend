pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '--> Instalando dependencias do projeto'
        bat(script: 'npm install', returnStdout: true, encoding: 'UTF-8')
        echo '--> Compilando projeto'
        bat(script: 'npm run build', returnStdout: true)
        sleep 5
      }
    }

    stage('Test') {
      steps {
        echo '--> Verificando problemas de sintaxe no código'
        bat(script: 'npm run lint', returnStatus: true, returnStdout: true)
        sleep 5
      }
    }

    stage('Deploy') {
      steps {
        input 'Realizar deploy no ambiente de producao?'
        bat(script: 'git push heroku jenkins:master', returnStatus: true, returnStdout: true)
      }
    }

  }
  environment {
    PORT = '3000'
  }
}