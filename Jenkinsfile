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
                sh 'npm install' 
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("lab11") 
                }
            }
        }
        
        stage('Run Docker Image') {
            steps {
                script {
                    docker.run("lab11") 
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', '1212') {
                        docker.image("lab11").push("latest") 
                    }
                }
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
