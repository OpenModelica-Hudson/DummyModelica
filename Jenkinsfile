pipeline {
  agent any
  stages {
    stage('Syntax Check') {
      agent {
        docker {
          image 'openmodelica/openmodelica:nightly'
        }

      }
      steps {
        sh 'omc --help'
      }
    }
  }
}