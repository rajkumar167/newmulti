
pipeline {
    agent any  

    
    stages {
        stage('Build') {
            steps {
                echo 'this is only tesing with multibranch'
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

            post{
                changed{
                    // Will trigger only when job status changes: GREEN -> RED, RED -> GREEN, etc
            notifyStatusChangeViaEmail(currentBuild.currentResult)
                }
            }
        }
    }
}


