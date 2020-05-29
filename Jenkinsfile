pipeline {
  agent { docker { image 'python:3.8.3' } }
  stages {
    stage('build') {
      steps {
        sh 'pip3 --version'
        sh 'pip3 install --/var/lib/jenkins/workspace/anti-virus-lambda-pipeline -r requirements-dev.txt'
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
