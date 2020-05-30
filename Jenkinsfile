pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {
    stage('build') {
      steps {
        withEnv(["HOME=${env.WORKSPACE}"]) {
          sh "pip install -r requirements-dev.txt --user"
        }
      }
    }
    stage('unit-test') {
      steps {
        withEnv(["HOME=${env.WORKSPACE}"]) {
          sh "pip install -r requirements-dev.txt --user"
          sh 'nosetests'
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
