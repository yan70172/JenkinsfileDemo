pipeline {

  agent any

  stages {
    stage ("build") {
      steps {
        echo 'building the application ...'
      }
    }

    stage ("test") {
      when {
        expression {
          BRANCH_NAME == 'master'
        }
      }
      steps {
        echo 'testing the application ...'
      }
    }

    stage ("deploy") {
      steps {
        echo 'deploying the application ...'
      }
    }
  }
}
