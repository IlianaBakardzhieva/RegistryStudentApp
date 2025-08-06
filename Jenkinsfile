pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'npm install'
                    } else {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Start application and run tests') {
            steps {
                script {
                    sh 'npm start &'
                    sh 'npx wait-on http://localhost:8080'
                    sh 'npm test'
                }
            }
        }
    }

    post {
        always {
            echo 'CI pipeline completed'
        }
    }
}
