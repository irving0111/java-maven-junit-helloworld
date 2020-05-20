pipeline {
  agent any
  stages {
    stage('checkout project') {
      steps {
        checkout scm
      }
    }

    stage('test') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true clean package'
      }
    }

    stage('report') {
      parallel {
        stage('report') {
          steps {
            junit(allowEmptyResults: true, testResults: '**/target/surefire-reports/TEST-*.xml')
          }
        }

        stage('archive') {
          steps {
            archiveArtifacts 'target/*.jar'
          }
        }

      }
    }

  }
}