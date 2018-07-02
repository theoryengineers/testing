pipeline {
    agent {
        docker {
            image 'node:carbon-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install -g yarn'
                sh 'yarn'
            }
        }
        stage('Test') {
            steps {
                sh '${WORKSPACE}/jenkins/scripts/test.sh'
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