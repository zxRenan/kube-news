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
              docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
                    dockerapp.push('latest')
                    dockerapp.push("${env.BUILD_ID}")
              }      
            }        
          }   
        }
        
        stage ('Deploy kubernetes'){
          steps{
            withkubecofig([credentialsID: 'Kubeconfig']){
                sh 'kubectl apply -f ./k8s/deployment.yaml'
            }
          }
        }
    
   
   
   
   
    }
   
   


}

