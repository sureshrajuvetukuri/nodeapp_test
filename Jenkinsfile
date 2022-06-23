pipeline{
    agent (label 'linux')
    
    environment {
        DOCKERHUB_CREDENTIALS=credentials('Jenkins-pipeline')
    stages{
        stage('Git clone') {
            steps{
                git 'https://github.com/sureshrajuvetukuri/nodeapp_test.git'
            }
        }
        
        stage('maven build') {
            steps{
                sh 'mvn package'
            }
        }
        stage('Create Dockerimage') {
            steps{
                sh 'docker build -t sureshrajuvetukuri/nodeapp_test:latest .'
            }
        }
        
        stage('login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        
        stage('Push') {
        
            steps{
                sh 'docker push sureshrajuvetukuri/nodeapp_test:latest'
            }
        }
        
        post {
            always {
                sh 'docker logout'
            }
        }   
     }   
  }
}  
