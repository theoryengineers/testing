pipeline {
    // agent {
    //     docker {
    //         image 'mhart/alpine-node:8'
    //         args '-p 3000:3000'
    //     }
    // }
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Deploy') {
            steps {                
                sh 'docker --version'
                sh "docker run -d \
                    --name site-b \
                    --net reverse-proxy \
                    -e 'LETSENCRYPT_EMAIL=theoryengineers@gmail.com' \
                    -e 'LETSENCRYPT_HOST=b.theoryengineers.com' \
                    -e 'VIRTUAL_HOST=b.theoryengineers.com' httpd"
            }
        }
    //     stage('Build') {
    //         steps { 
    //             sh 'docker --version'         
    //             sh 'yarn'
    //             sh 'chmod -R 755 scripts'
    //         }
    //     }
    //     stage('Test') {
    //         steps {
    //             sh './scripts/test.sh'
    //         }
    //     }
    //     stage('Deliver') {
    //         steps {
    //             sh './scripts/deliver.sh'
    //             input message: 'Finished using the web site? (Click "Proceed" to continue)'
    //             sh './scripts/kill.sh'
    //         }
    //     }
    // }
}