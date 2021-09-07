pipeline {
  agent any
  stages {
    stage('Stage1') {
      steps {
        sh 'echo "Hello Stage 1"'
        stash(name: 'variable1', allowEmpty: true)
      }
    }

    stage('Stage2') {
      parallel {
        stage('Stage2') {
          steps {
            sh 'echo "Hello Stage2->Step1"'
            echo 'Hello Stage2->Step2'
          }
        }

        stage('Stage3') {
          steps {
            echo 'Hello Stage3'
            catchError(catchInterruptions: true, stageResult: 'failure', buildResult: 'failure', message: 'Build failed') {
              echo 'Over!!'
            }

          }
        }

      }
    }

    stage('Stage4') {
      steps {
        echo 'Hello Stage4'
      }
    }

  }
  environment {
    list = 'a,b,c'
  }
}