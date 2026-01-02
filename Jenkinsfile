pipeline {
    agent any


    stages {

        stage('cleanws') {
            steps {
                cleanWs()
            }
        }

        stage('Code') {
            steps {
                git 'https://github.com/gopi-wp/app.py.git'
            }
        }
        stage('image build') {
            steps {
               sh ' docker build -t app3 .'
         }
        }
       stage('tag and push') {
          steps {
              script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                     sh 'docker tag app3 gopibrahmaiah/library:app-v3'
                     sh 'docker push gopibrahmaiah/library:app-v3'
                  }
              }
           }
         }
       }
    }
