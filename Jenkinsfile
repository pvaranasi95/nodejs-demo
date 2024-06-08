pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('pvaranasi-dockerhub')
    }
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
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
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

