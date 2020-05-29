pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {
    stage('build') {
      steps {
        sh 'pip install -r requirements-dev.txt'
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
