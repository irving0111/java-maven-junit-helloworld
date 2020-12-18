pipeline {
  agent any
  stages {
    stage('checkout project') {
      steps {
        checkout scm
      }
    }

    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }

  }
}