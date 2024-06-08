pipeline {
    agent any 
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/pvaranasi95/nodejs-demo.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t pvaranasi/nodeapp:1 .'
            }
        }
        
        stage('push image') {
            steps{
                sh 'docker push pvaranasi/nodeapp:1'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}

