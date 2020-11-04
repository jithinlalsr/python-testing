pipeline {
    environment {
    registry = "jithinlalsr/docker_learn"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }   
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'python3 test_calc.py'
                  }  
                }    
       stage('Build') {
            steps{
              script {
                 dockerImage = docker.build "${GIT_COMMIT}"
                     }    
                 }
              }     
// Push your image 
       stage('Push') {
             steps { 
		script {
                       docker.withRegistry('', 'dockerhub') {
                                 dockerImage.push()
		                       }   
		         } 
	               }          
                    } 
            }
         }	
