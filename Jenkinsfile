
pipeline {

  agent any

  environment {
    NEW_VERSION = '1.3.0'

    CODE_CHANGE = true
    
  }

  stages {
    stage ("build") {
      when {
        expression {
          BRANCH_NAME == 'master' && CODE_CHANGE == true
        }
      }
      
      steps {
        echo 'building the application ...'
        echo 'building version ${NEW_VERSION}'
        echo "building version ${NEW_VERSION}"
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

        withCredentials([
          usernamePassword(credentials: 'MyGitHub', usernameVariable: USER, passwordVariable: PWD)
        ]){
          echo "User: ${USER}"
          echo "Password: ${PWD}"
        }
        
      }
    }
  }
}
