pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sakib1133/school-management-devops-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('App') {
                    sh 'npm install'
                }
            }
        }

        stage('Verify Environment') {
            steps {
                dir('App') {
                    sh 'node -v'
                    sh 'npm -v'
                }
            }
        }

        stage('Application Check') {
            steps {
                dir('App') {
                    sh 'test -f package.json'
                    echo 'package.json found'
                }
            }
        }

        stage('Build') {
            steps {
                echo 'No build step required for this Express application'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
