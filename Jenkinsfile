pipeline {
    agent any

    environment {
        VERCEL_PROJECT_NAME = 'learn-jenkins-app'
        VERCEL_TOKEN = credentials('vercel-token')
    }

    stages {
        stage('Install') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Deploy') {
            steps {
                sh 'npm install -g vercel'
                sh 'vercel deploy --prod --token $VERCEL_TOKEN --yes'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished'
        }
    }
}
