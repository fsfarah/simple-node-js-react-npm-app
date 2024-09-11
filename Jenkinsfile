pipeline {
    agent {
        docker { image 'node:20.17.0-alpine3.20' }
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
    }
}
