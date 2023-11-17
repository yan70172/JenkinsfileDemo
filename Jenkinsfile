CODE_CHANGE = true
pipeline {

  agent any

  parameters {
    // string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
    choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }

  stages {
    stage ("build") {

      when {
        expression {
          params.executeTests
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
        echo "deploying version ${params.VERSION}"
      }
    }
  }
  post {
    always {
      echo 'post Always'
    }
    
  }
}
