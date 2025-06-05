pipeline {
    agent any

    environment {
        NODE_VERSION = '18.x'
    }

    tools {
        nodejs 'nodejs18'  // това трябва да е името на NodeJS tool-а в Jenkins
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
                bat 'start /b npm start'  // стартира app на заден фон в Windows
                bat 'wait-on http://localhost:8090' // изисква wait-on да е инсталиран глобално
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
