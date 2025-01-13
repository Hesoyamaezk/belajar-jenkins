pipeline {
  agent {
    node {
      label 'linux && java11'
    }
  }

  stages{
    
    stage('heloo') {
      steps {
        echo('hello pipline')
      }
    }
    
    stage('Test') {
      steps {
        echo('hello test')
      }
    }

    stage('Build') {
      steps {
        echo('hello build')
      }
    } 
    
    stage('Deploy') {
      steps {
        echo('hello deploy')
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


