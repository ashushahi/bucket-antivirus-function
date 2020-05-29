pipeline {
  agent { docker { image 'python:alpine3.10' } }
  stages {
    stage('build') {
      steps {
        sh 'pip3 --version'
        sh 'python --version'
        sh 'apk update'
        sh 'apk upgrade'
        sh 'apk add bash'
        sh 'where bash'
        sh 'python -m venv venv'
        sh 'source venv/bin/activate'
        sh 'pip3 install -r requirements-dev.txt'
      }
    }
    stage('unit-test') {
      steps {
        sh 'nosetests'
      }
      
      post {
        always {
          junit 'nosetests.xml'
        }
      } 
    }
    stage('integration-test') {
      steps {
        sh 'nosetests'
      }
      post {
        always {
          junit 'nosetests.xml'
        }
      }
    }
  }
}
