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
                 withCredentials([usernamePassword( credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
		script {
                       docker.withRegistry('', 'dockerhub') {
                                 sh "docker login -u ${USERNAME} -p ${PASSWORD} docker.io"
                                 dockerImage.push()
		                       }   
		                } 
		           }
                        }           
                    } 
            }
         }	
