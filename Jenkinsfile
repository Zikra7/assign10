pipeline {
    agent any 
    environment {
        //once you sign up for Docker hub, use that user_id here
        registry = "zikra/hello-docker-java"
        //- update your credentials ID after creating credentials for connecting to Docker Hub
        registryCredential = 'dockerid'
        dockerImage = ''
    }
    
    stages {
        stage('Cloning Git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://hub.docker.com/repository/docker/zikra/hello-docker-java']]])       
            }
        }
    
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
    
    
