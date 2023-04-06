pipeline {
    agent {
        docker {            
            image 'node:lts-buster-slim'
            args '-p 3000:3000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
        stage('Build') { 
            steps {
                sh 'npm install'
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
                sh 'npm install' 
            }
        }
    }
}