pipeline {
  agent {
  }
    stages {
    stage('Syntax Check') {
      parallel {
        stage('OpenModelica') {
  agent {
    docker {
      image 'openmodelica/openmodelica:nightly'
    }
  }
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
        stage('moparser') {
          agent {
            docker {
              image 'openmodelica/moparser'
            }

          }
          steps {
            sh 'moparser -r -v 2.2 BioChem'
          }
        }
      }
    }
  }
}
