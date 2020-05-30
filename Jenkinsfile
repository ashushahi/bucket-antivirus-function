pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {
    stage('build') {
      steps {
        sh 'whereis python3.7'
        sh 'python3.7 -m venv venv'
        sh '. ./venv/bin/activate'
        sh 'whereis python3.7'
        sh "pip3 install -r requirements-dev.txt"
        sh 'nosetests'
      }
    }
    stage('unit-test') {
      steps {
        withEnv(["HOME=${env.WORKSPACE}"]) {
          sh "pip install -r requirements-dev.txt --user"
          sh './.local/bin/nosetests'
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
