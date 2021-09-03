pipeline {
  agent any
  stages {
    stage('CreateDynamicStage') {
      steps {
        step {
          def tests = params.Tests.split(',')
          for (int i = 0; i < tests.length; i++) {
            stage("Test ${tests[i]}") {
              sh 'echo hello!'
            }
          }
        }
      }
    }

  }
}
