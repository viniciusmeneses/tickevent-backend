pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '--> Instalando dependências do projeto'
        bat(script: 'npm install', returnStatus: true, returnStdout: true)
        echo '--> Compilando projeto'
        bat(script: 'npm run build', returnStatus: true, returnStdout: true)
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
        input 'Realizar deploy no ambiente de produção?'
        bat(script: 'git push heroku jenkins:master', returnStatus: true, returnStdout: true)
      }
    }

  }
  environment {
    PORT = '3000'
  }
}