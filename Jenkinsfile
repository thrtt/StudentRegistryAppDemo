pipeline {
    agent any

    tools {
        nodejs 'nodejs18'  
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/thrtt/StudentRegistryAppDemo.git'
            }
        }

        stage('Install dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Start application and run tests') {
            steps {
                bat 'start /b npm start'
                bat 'npx wait-on http://localhost:8090'
                bat 'npm test'
            }
        }
    }

    post {
        always {
            echo 'CI pipeline completed'
        }
    }
}
#..