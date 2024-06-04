pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/MaleehaYounas/SCD_lab11'
            }
        }
        
        stage('Dependency Installation') {
            steps {
                bat 'npm install' 
            }
        }
        
         stage('Build Docker Image') {
            steps {
                 bat 'echo docker build -t lab11 .'
            }
        }
        
        stage('Run Docker Image') {
            steps {
                bat 'echo docker run -d -p 8086:80 lab11' 
            }
        }
        
        
        stage('Push Docker Image') {
            steps {
                bat 'echo script { docker.withRegistry(https://registry.hub.docker.com, 1212) { docker.image("lab11").push("latest") }'
            }
        }
    }
    
    post {
        success {
            echo 'Deployment successful! Congratulations!'
        }
        failure {
            echo 'Deployment failed! Check logs for errors.'
        }
    }
}
