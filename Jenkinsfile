pipeline {
  agent { docker { image 'python:3.7.7' } }
  stages {

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
    
    tage('build') {
      steps {
        sh 'whereis python3.7'
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
