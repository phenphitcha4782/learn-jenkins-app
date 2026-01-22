pipeline {

    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
    }

    environment {
environment {
    VERCEL_PROJECT_NAME = 'learn-jenkins-app'
    VERCEL_TOKEN = credentials('l1McyCDQe4lKknHJh6x0Po9S')
}

    }

    stages {

        stage('Build') {
            steps {
                sh 'npm ci'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'npm install vercel'
                sh './node_modules/.bin/vercel deploy --prod --prebuilt'
            }
        }
    }

    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
