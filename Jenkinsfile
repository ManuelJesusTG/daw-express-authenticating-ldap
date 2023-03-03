pipeline {
  agent {
    docker {
      image 'node:lts-bullseye-slim'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }

    stage('Deliver/Despliegue') {
      steps {
        sh 'npm start & sleep 1 .pidfile'
        input 'Para terminar de usar el sitio web click en el boton "Proceed"'
        sh 'kill $(cat .pidfile)'
      }
    }

  }
}