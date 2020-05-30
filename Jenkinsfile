pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {
    stage('build') {
      steps {
        sh 'pip3 --version'
        sh 'python --version'
        sh 'python -m venv venv'
        sh '. ./venv/bin/activate'
        sh 'rm -f -- .local'
        sh 'ls -a'
        sh 'mkdir .local'
        sh 'chmod -R 777 .local'
        sh 'ls -a'
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
