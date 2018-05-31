pipeline {
  agent any
  stages {
    stage('Syntax Check') {
      steps {
        timeout(time: 60, activity: true) {
          sh 'omc --help'
        }

      }
    }
  }
}