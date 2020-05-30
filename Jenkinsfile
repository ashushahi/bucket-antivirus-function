pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {
    stage('build') {
      steps {
        sh 'pip3 --version'
        sh 'python --version'
        sh 'python -m venv venv'
        sh '. ./venv/bin/activate'
        sh 'pip3 install --install-option="--prefix=./venv" boto3'
        sh 'pip3 install coverage'
        sh 'pip3 install mock'
        sh 'pip3 install nose'
        sh 'pip3 install nose-testconfig'
        sh 'pip3 install requests'
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
