pipeline {
    agent none

    environment {
        AUTHOR = 'Ahmad wizam'
        EMAIL = 'Ahmadwizam12@gmail.com'
      }

    stages {

      stage('Preparation') {
        environment {
            APP = credentials('izam_ID')
          }
        agent {
          node {
             label 'linux && java11'
          }
        }
        steps {
          echo "Author : ${env.AUTHOR}"
          echo "Email : ${env.EMAIL}"
          echo "Start Job : ${env.JOB_NAME}"
          echo "Start Building.... : ${env.BUILD_NUMBER}"
          echo "Branch Name : ${env.BRANCH_NAME}"
          echo "App User : ${APP_USR}"
          echo "App Password : ${APP_PSW}"
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
            for (int i = 0; i < 5; i++) {
              echo 'Script ${i}'
            }
          }
          echo 'Start Building....'
          sh './mvnw clean compile test-compile'
          echo 'Finished Building....'
        }
      }

      stage('Test') {
        agent {
          node {
             label 'linux && java11'
          }
        }
        steps {
          script {
            def data = [
              'firstName': 'John',
              'lastName': 'Doe',
            ]
            writeJSON (file: 'data.json', json: data)
          }
          echo 'Testing....'
          sh './mvnw test'
          echo 'Finished testing....'
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
