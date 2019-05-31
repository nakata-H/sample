pipeline {
  agent any
  stages {
    stage('compile') {
      parallel {
        stage('compile') {
          steps {
            sh 'javac Sample.java'
          }
        }
        stage('parallel1') {
          steps {
            sh 'echo "parallel node1"'
          }
        }
      }
    }
    stage('chmod') {
      steps {
        sh 'chmod 777 Sample.class'
      }
    }
    stage('execute_classfile') {
      parallel {
        stage('execute_classfile') {
          steps {
            sh 'java Sample'
          }
        }
        stage('parallel2') {
          steps {
            sh '''echo "-------------parallel2-----------"
env
echo "-------------parallel2-----------"'''
          }
        }
        stage('parallel3') {
          steps {
            sh 'echo "parallel3"'
          }
        }
      }
    }
    stage('save_product') {
      steps {
        archiveArtifacts(artifacts: '*.class', allowEmptyArchive: true, fingerprint: true, onlyIfSuccessful: true)
      }
    }
  }
}
