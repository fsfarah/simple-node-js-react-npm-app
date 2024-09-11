pipeline {
    agent {
        docker { 
            image 'node:20.17.0-alpine3.20'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Test') { 
            steps {
                sh 'ls -l ./jenkins/scripts/test.sh'  // Optional: Verify that the script exists and is executable
                sh './jenkins/scripts/test.sh' 
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                archiveArtifacts artifacts: 'build/**/*', allowEmptyArchive: true
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
