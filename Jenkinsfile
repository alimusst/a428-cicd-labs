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
    stage('test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('deploy') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        sh 'npm install -g heroku'
        sh 'heroku login'
      }
    }
  }
}