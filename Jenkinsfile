pipeline {
    agent none

    stages {

      stage('Build') {
        agent {
          node {
             label 'linux && java11'
          }
        }
        steps {
          echo 'Building....'
        }
      }

      stage('Test') {
        agent {
          node {
             label 'linux && java11'
          }
        }
        steps {
          echo 'Testing....'
        }
      }

      stage('Deploy') {
        agent {
          node {
             label 'linux && java11'
          }
        }
        steps {
          echo 'Deploying....'
        }
      }

    }

    post {
      always {
        echo 'This will always run'
      }
      success {
        echo 'This will run only if successful'
      }
      failure {
          echo 'Oh no, the pipeline failed!'
      }
      cleanup {
          echo 'This will always run'
      }
    }
}
