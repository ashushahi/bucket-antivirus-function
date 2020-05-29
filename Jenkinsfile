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
        sh 'nosetests ./tests/unit/ --with-xunit'
      }   
    }
    stage('integration-test') {
      steps {
        sh 'nosetests ./tests/integration/integration_test.py --tc=awsregion:eu-west-1 --tc=configbucket:emn-dev-config --tc=propertyfile:emn-antivirus-service-integration.properties --with-xunit'
      }   
    }
  }
}
