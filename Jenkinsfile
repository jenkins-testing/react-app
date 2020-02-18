pipeline {
    agent {
        docker {
            image 'node:10-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
        MTFA_MOUNT_POINT = '/mtfa'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "Mount point ${env.MTFA_MOUNT_POINT}"
                sh './scripts/test.sh'
            }
        }
        // stage('Deliver') {
        //     steps {
        //         sh './scripts/deliver.sh'
        //         input message: 'Finished using the web site? (Click "Proceed" to continue)'
        //         sh './scripts/kill.sh'
        //     }
        // }
    }
}