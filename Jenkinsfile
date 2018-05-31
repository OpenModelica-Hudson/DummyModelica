pipeline {
  agent {
    docker {
      image 'openmodelica/openmodelica:nightly'
    }

  }
  stages {
    stage('Syntax Check') {
      steps {
        sh '''echo > check.mos << EOL
b := loadFile("BioChem/package.mo");getErrorString();
if b then
  exit(0);
end if;
exit(1);
EOL
omc check.mos'''
      }
    }
  }
}