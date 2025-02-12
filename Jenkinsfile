pipeline {
    agent any

    stages {  
        stage('NPM Install') {
            steps {
                sh 'npm install' 
            }
        }
        stage('Run NPM Audit Tests') {
            steps {
                sh 'npm audit' 
            }
        }
        stage('Run Integration Tests') {
            steps {
                sh 'npm run test' 
            }
        }
    }
}
