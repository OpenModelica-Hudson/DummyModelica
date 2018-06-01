pipeline {
  agent any
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
            sh '''
cat - > check.mos << EOF
b := loadFile("BioChem/package.mo", uses=false);
(numMessages,numError,numWarning):=countMessages();
getErrorString();
if b and numError==0 and numWarning==0 then
  exit(0);
end if;
exit(1);
EOF
omc check.mos
'''
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
