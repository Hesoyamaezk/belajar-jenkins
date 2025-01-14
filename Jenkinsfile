pipeline {
    agent none

    environment {
        AUTHOR = 'Ahmad wizam'
        EMAIL = 'Ahmadwizam12@gmail.com'
    }

    triggers {
        //cron('*/5 * * * *')
        pollSCM('*/5 * * * *')
        //upstream(upstreamProjects: 'my-job', threshold: 'SUCCESS')
    }

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'master', description: 'Branch to build')
        text(name: 'APP_USR', defaultValue: 'admin', description: 'App Username')
        booleanParam(name: 'DEPLOY', defaultValue: true, description: 'Deploy after build')
        choice(name: 'CHOICE', choices: ['one', 'two', 'three'], description: 'Pick something')
        password(name: 'APP_PSW', defaultValue: 'admin', description: 'App Password') 
    }

    options {
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'MINUTES')
    }



    stages {

      stage ('parameter') {
        agent {
          node {
             label 'linux && java11'
          }
        }
        steps {
          echo "Branch Name : ${params.BRANCH_NAME}"
          echo "App User : ${params.APP_USR}"
          echo "Deploy : ${params.DEPLOY}"
          echo "Choice : ${params.CHOICE}"
          echo "App Password : ${params.APP_PSW}"
        }
      }

      stage('Preparation') {
        environment {
            APP = credentials("izam_ID")
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
          sh 'echo "App Password : $APP_PSW" > "rahasia.txt" '
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
