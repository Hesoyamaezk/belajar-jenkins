pipeline {
    agent none

    environment {
        AUTHOR = 'Ahmad wizam'
        EMAIL = 'Ahmadwizam12@gmail.com'
    }

//     triggers {
//        cron('*/5 * * * *')
//        pollSCM('*/5 * * * *')
//        upstream(upstreamProjects: 'my-job', threshold: 'SUCCESS')
//    }
    parameters {
        string(name: "NAME", defaultValue: "Guest", description: "What is your name?")
        text(name: "DESCRIPTION", defaultValue: "Guest", description: "Tell me about you")
        booleanParam(name: "DEPLOY", defaultValue: false, description: "Need to Deploy?")
        choice(name: "SOCIAL_MEDIA", choices: ['Instagram', 'Facebook', 'Twitter'], description: "Which Social Media?")
        password(name: "SECRET", defaultValue: "", description: "Encrypt Key")
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
          echo "Hello ${params.NAME}"
          echo "You description is ${params.DESCRIPTION}"
          echo "Your social medis is ${params.SOCIAL_MEDIA}"
          echo "Need to deploy : ${params.DEPLOY} to deploy!"
          echo "Your secret is ${params.SECRET}"
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
        input {
          message 'Do you want to deploy?'
          ok 'Yes'
          submitter 'admin'
        }
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
