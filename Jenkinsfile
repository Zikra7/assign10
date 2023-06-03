pipeline {
    agent any 
    environment {
        //once you sign up for Docker hub, use that user_id here
        registry = "zikra/hello-docker-java"
        //- update your credentials ID after creating credentials for connecting to Docker Hub
        registryCredential = 'dockerid'
        dockerImage = ''
    }
    
   stages
    {
    
    // Building Docker images
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry
        }
      }
    }
    
     // Uploading Docker images into Docker Hub
    stage('Upload Image') {
     steps{    
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            }
        }
      }
    }
    } 
}
    
    
