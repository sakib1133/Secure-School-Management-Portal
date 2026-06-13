pipeline {
agent any

```
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

    stage('Verify Application') {
        steps {
            dir('App') {
                sh 'node --version'
                sh 'npm --version'
            }
        }
    }

    stage('Build') {
        steps {
            echo 'No build step required for Express application'
        }
    }
}

post {
    success {
        echo 'Pipeline completed successfully'
    }

    failure {
        echo 'Pipeline failed'
    }
}
```

}
