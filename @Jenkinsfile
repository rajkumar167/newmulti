
pipeline {
    agent any  

    
    stages {
        stage('Build') {
            steps {
                echo 'build this project'
            }
        }
        stage('Test') {
            steps {
                echo ' tetesting this stage till test not pass'
            }
        }
        stage('Deliver for development') {
            when {
                branch 'dev'
            }
            steps {
                script{
                    sh 'docker build -t  rajkumar167/rajdocker:v2 .'
                }
                
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'
            }
            steps {
                script{
                    sh 'docker push rajkumar167/rajdocker:v2'
                }
                
            }
        }
    }
}


