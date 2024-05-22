 pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = "/path/to/code"
        TESTING_ENVIRONMENT = "testing-environment"
        PRODUCTION_ENVIRONMENT = "production-environment"
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Fetching source code from ${env.DIRECTORY_PATH}"
                echo "Compiling code and generating artifacts"
            }
        }
        
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }
        
        stage('Code Quality Check') {
            steps {
                echo "Checking code quality"
            }
        }
        
        stage('Deploy') {
   …
[7:53 pm, 22/05/2024] Edmund Aptech: pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = "/path/to/code"
        TESTING_ENVIRONMENT = "testing-environment"
        PRODUCTION_ENVIRONMENT = "production-environment"
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Fetching source code from ${env.DIRECTORY_PATH}"
                echo "Compiling code and generating artifacts"
            }
        }
        
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }
        
        stage('Code Quality Check') {
            steps {
                echo "Checking code quality"
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying application to ${env.TESTING_ENVIRONMENT}"
            }
        }
        
        stage('Approval') {
            steps {is
                sh "sleep 10"
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying code to ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    
post {
        success {
            mail to: 'okoraforokechukwu@gmail.com', subject: 'Pipeline Success', body: "${env.BUILD_URL}"
         echo "Sending Pipeline E-mail to Senior Software engineer paul"  
        }
    }
}
