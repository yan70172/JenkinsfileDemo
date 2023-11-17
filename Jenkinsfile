CODE_CHANGE = true
pipeline {

  agent any

  environment {
    NEW_VERSION = '1.3.0'

    // define credentials in Jenkin GUI
    // plugin 'Credentials Binding' is needed.
    // credentials() binds the crendentials to env variable, parameter should be credential's ID
    SERVER_CREDENTIALS = credentials('MyGitHub')
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
        echo "deploying with ${SERVER_CREDENTIALS}"
      }
    }
  }
}
