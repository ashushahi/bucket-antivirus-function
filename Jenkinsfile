pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {
    stage('build') {
      steps {
        sh 'python -m venv venv'
        sh  'source venv/bin/activate'
        sh /bin/bash -c "source venv/bin/activate"
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
