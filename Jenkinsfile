pipeline {
    agent {
        docker {
            image 'node:14'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
        HOME = '.'
    }
    stages {
        stage('Permit') {
            steps {
                sh 'sudo chmod -R 777 ./jenkins/scripts/*.sh'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'pwd'
                sh 'dir'
                sh 'pwd'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}