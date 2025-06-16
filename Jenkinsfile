pipeline {
    
    agent any
    
    stages{
        stage('CodeScan'){
            steps{
                sh 'trivy fs . -o result.html'
                sh 'cat result.html'
                
                
            }
        }
        stage('dockerLogin')
            steps{
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 345594563748.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
        stage('dockerImageBuild'){
            steps{
                sh 'docker build -t jenkins-ci .'
            }
        }

        stage('dockerImageTag'){
            steps{
                sh 'docker tag jenkins-ci:latest 345594563748.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
            }
        }

        stage('PushImage'){
            steps{
                sh 'docker push 345594563748.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
            }
        }
    }

