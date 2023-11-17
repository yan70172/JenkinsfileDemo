def gv

pipeline {

  agent any

  parameters {
    // string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
    choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }

  stages {

    stage("init"){
      steps {
        script {
          gv = load "script.groovy"
        }
      }
    }
    
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
          usernamePassword(credentialsId: 'MyGitHub', usernameVariable: USER, passwordVariable: PWD)
        ]){
          echo "User: ${USER}"
          echo "Password: ${PWD}"
        }
        
      }
    }
  }
}
