CODE_CHANGE = getGitChanges()
pipeline {

  agent any

  stages {
    stage ("build") {
      when {
        expression {
          BRANCH_NAME == 'master' && CODE_CHANGE == true
        }
      }
      
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
