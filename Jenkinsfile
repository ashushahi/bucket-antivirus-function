pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {
    stage('build') {
      steps {
        sh 'whereis python3.7'
      }
    }
    stage('unit-test') {
      steps {
        withEnv(["HOME=${env.WORKSPACE}"]) {
          sh "pip install -r requirements-dev.txt --user"
          sh './.local/bin/nosetests --with-xunit'
        }
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
