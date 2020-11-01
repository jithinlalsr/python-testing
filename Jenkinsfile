pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                powershell 'python test_calc.py'
            }
        }
    }
}
