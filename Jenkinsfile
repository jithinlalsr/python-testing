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
    }
}
