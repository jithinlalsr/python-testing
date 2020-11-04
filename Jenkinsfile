pipeline {
	    
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
             withCredentials([usernamePassword( credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                   docker.withRegistry('https://registry.hub.docker.com/', 'dockerhub') {
                       sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                       dockerImage.push()
		   }
        }
}
