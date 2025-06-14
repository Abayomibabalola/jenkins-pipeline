pipeline {
    
    agent any
    
    stages{
        stage('Clone'){
            steps{
                sh 'echo "clone"'
            }
        }

        stage('Test'){
            steps{
                sh 'echo "test"'
            }
        }

        stage('Create File'){
            steps{
                sh 'touch text-${BUILD_NUMBER}.txt'
            }
        }
    }
}
