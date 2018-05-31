pipeline {
  agent {
    docker {
      image 'openmodelica/openmodelica:nightly'
    }

  }
  stages {
    stage('Syntax Check') {
      steps {
        sh '''cat - > check.mos << EOL
b := loadFile("BioChem/package.mo");getErrorString();
if b then
  exit(0);
end if;
exit(1);
EOL
ls
cat check.mos
omc check.mos'''
      }
    }
  }
}