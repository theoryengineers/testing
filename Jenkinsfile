pipeline {
    agent {
        docker {
            image 'mhart/alpine-node:8'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'ls'
                sh 'pwd'
                sh 'yarn --version'
                sh 'yarn'   
                sh 'yarn help'

            }
        }
        stage('Test') {
            steps {
                sh "ls"
                sh "jenkins/scripts/test.sh"
            }
        }
        stage('Deliver') {
            steps {
                sh '${WORKSPACE}/jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh '${WORKSPACE}/jenkins/scripts/kill.sh'
            }
        }
    }
}