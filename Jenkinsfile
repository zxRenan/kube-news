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

        stage ('Push Docker Image') {
          steps {
            script {
              docker.withRegistry('https://registry.hub.docker.com')
                    dockerapp.push('latest')
                    dockerapp.push("${env.BUILD_ID}")
            }        
          }   
        }
        
    
   
   
   
   
    }
   
   


}

