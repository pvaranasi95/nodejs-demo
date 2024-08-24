pipeline {
    agent {
        node { label 'Windows1' }
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/pvaranasi95/nodejs-demo.git'
            }
        }

        stage('Build docker image') {
            steps {  
            bat 'docker build -t pvaranasi/nodeapp:1 .'
            }
        }
        
        stage('push image') {
            steps{
                bat 'docker push pvaranasi/nodeapp:1'
            }
        }
        stage('Container') {
            steps{
                bat 'docker run -d -p 3000:3000 --name nodejs1 pvaranasi/nodeapp:1'
            }
        }
}
}

