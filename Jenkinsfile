pipeline {
    environment {
    registry = "jithinlalsr/docker_learn"
    registryCredential = 'dockerhub'
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
                 sh 'docker build -t "${GIT_COMMIT}" .'
                 sh 'docker tag "${GIT_COMMIT}:latest" "${registry}:latest"'
                                      }    
                 }
              }     
// Push your image to docker
       stage('Push') {
             steps { 
		script {
                       docker.withRegistry('', 'dockerhub') {
                                 sh 'docker push "${registry}:latest"'
		                       }   
		         } 
	               }          
                    } 
            }
         }	
