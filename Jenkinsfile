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

    stage('report') {
      parallel {
        stage('report') {
          steps {
            archiveArtifacts 'target/*.jar'
          }
        }

        stage('junit') {
          steps {
            sh 'mvn clean package'
          }
        }

      }
    }

  }
}