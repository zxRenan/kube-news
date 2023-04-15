pipeline{
    agent any

    stages {

        stage ('Build Docker Image'){
            steps {
              script{
                dockerapp = docker.build("zxrenanzx/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
              }
            }
        }
    }
}