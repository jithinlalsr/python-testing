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
	stage('Push') { 
            steps { 
              withCredentials([usernamePassword( registryCredential, usernameVariable: 'USER', passwordVariable: 'PASSWORD')]) {
                script { 
		    bat "docker login -u $USER -p $PASSWORD ${registry}"	
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push() 
                    }
                 } 
	      }	      
            }
	} 
    }
}
