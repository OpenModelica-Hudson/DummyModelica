pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Syntax Check') {
      agent {
        docker {
          image 'openmodelica/openmodelica:nightly'
        }

      }
      steps {
        timeout(time: 60, activity: true) {
          sh 'omc --help'
        }

      }
    }
  }
}