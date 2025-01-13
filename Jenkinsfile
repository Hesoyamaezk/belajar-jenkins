pipeline {
  agent {
    node {
      label 'linux && java11'
    }
  }

  stages{
    
    stage('Build') {
      steps {

        script {
          for (int i = 0; i < 10; i++) {
            echo ('Script ${i}')
          }
        }

        echo('Start Build')
        sh('./mvnw clean compile test-compile')
        echo('Finish Build')
      }
    }

    stage('test') {
      steps {
        echo('Start Test')
        sh('./mvnw test')
        echo('Finish Test')
      }
    } 
    
    stage('Deploy') {
      steps {
        echo('hello deploy')
        echo('hello deploy1')
      }
    }

  }
  
  post{
    always {
      echo 'I will always say hello again!'
    }
    success {
      echo 'Yay, susccess'
    }
    failure {
      echo 'Oh no, failure'
    }
    cleanup {
      echo "Don't care success or error"
    }
  }


}


