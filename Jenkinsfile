pipeline {
  agent none

  stages{


    stage('Preparation') {
      agent {
        node {
          label 'linux && java11'
        }
      }
      steps {
        echo('Start Preparation Job : ${env.JOB_NAME}')
        echo('Start build number :  ${env.BUILD_NUMBER}')
        echo('Branch Name : ${env.BRANCH_NAME}')
      }


    stage('Build') {
     agent {
        node {
          label 'linux && java11'
        }
      }
      steps {

        script {
          def data =  [
              'firstName': 'ahmad',
              'lastName': 'wizam'
          ]
          writeJSON(file: 'data.json', json: data)
        }

        echo('Start Build')
        sh('./mvnw clean compile test-compile')
        echo('Finish Build')
      }
    }

    stage('Build') {
     agent {
        node {
          label 'linux && java11'
        }
      }
      steps {

        script {
          def data =  [
              'firstName': 'ahmad',
              'lastName': 'wizam'
          ]
          writeJSON(file: 'data.json', json: data)
        }

        echo('Start Build')
        sh('./mvnw clean compile test-compile')
        echo('Finish Build')
      }
    }

    stage('test') {
      agent {
        node {
          label 'linux && java11'
        }
      }
      steps {
        echo('Start Test')
        sh('./mvnw test')
        echo('Finish Test')
      }
    } 
    
    stage('Deploy') { 
      agent {
        node {
          label 'linux && java11'
        }
      }
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
