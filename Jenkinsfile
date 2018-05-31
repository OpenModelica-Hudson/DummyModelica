pipeline {
  agent any
  stages {
    stage('Syntax Check') {
      docker.image('openmodelica/openmodelica:nightly').inside {
        sh 'omc --help'
      }
    }
  }
}
