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

        stage('Deploy to Staging') {
            steps {
                sh 'echo Deploying to Staging Environment...'
                sh 'export NODE_ENV=staging && docker-compose up -d'
            }
        }

        stage('Approval to Deploy to Production') {
            steps {
                input message: 'Proceed with Production Deployment?', ok: 'Deploy'
            }
        }

        stage('Deploy to Production') {
            steps {
                sh 'echo Deploying to Production...'
                sh 'export NODE_ENV=production && docker-compose up -d'
            }
        }
    }
}
