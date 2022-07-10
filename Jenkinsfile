pipeline{
    agent any
    
    environment {
        DOCKERHUB_CREDENTIALS=credentials('Docker-Project')
    }    
    
    stages{
        
        stage('gitclone') {
            steps{
                git 'https://github.com/sureshrajuvetukuri/nodeapp_test.git'
            }
        }
        
        stage('Build') {
            steps{
                sh 'docker build -t suresh394/nodeapp_test:latest .'
            }
        }
        
        stage('login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        
        stage('Push') {
        
            steps{
                sh 'docker image push suresh394/nodeapp_test:latest'
            }
        }
     }   
  }  
