pipeline {
    agent any

   

    environment {
        FRONTEND_DIR = "frontend"
        BACKEND_DIR = "backend"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/virat9999/-my-fullstack-project.git'
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                dir("${BACKEND_DIR}") {
                    bat 'npm install'
                }
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                dir("${FRONTEND_DIR}") {
                    bat 'npm install'
                }
            }
        }

        stage('Run Backend Tests') {
            steps {
                dir("${BACKEND_DIR}") {
                    bat 'npm test'
                }
            }
        }

        stage('Run Frontend Tests') {
            steps {
                dir("${FRONTEND_DIR}") {
                    bat 'npm test'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir("${FRONTEND_DIR}") {
                    bat 'npm run build'
                }
            }
        }

        stage('Package Backend') {
            steps {
                dir("${BACKEND_DIR}") {
                    bat 'npm run build'
                }
            }
        }
    }

    post {
        success {
            echo "✅ Fullstack CI pipeline completed successfully!"
        }
        failure {
            echo "❌ Pipeline failed!"
        }
    }
}
