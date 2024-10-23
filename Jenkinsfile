pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'myimg1'
        PORT = '8082'
    }
    
    stages {
        stage('Checkout the code from GitHub') {
            steps {
                git url: 'https://github.com/kolleykalyani/health-care-project/'
                echo 'Checked out code from GitHub'
            }
        }
        
        stage('Code Compile with Kalyani') {
            steps {
                echo 'Starting compilation'
                sh 'mvn compile'
            }
        }
        
        stage('Code Testing with Kalyani') {
            steps {
                echo 'Running tests'
                sh 'mvn test'
            }
        }
        
        stage('QA Check with Kalyani') {
            steps {
                echo 'Running code quality checks'
                sh 'mvn checkstyle:checkstyle'
            }
        }
        
        stage('Package with Kalyani') {
            steps {
                echo 'Packaging the application'
                sh 'mvn package'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image'
                sh "docker build -t ${DOCKER_IMAGE} ."
            }
        }
        
        stage('Run Docker Container') {
            steps {
                echo 'Running Docker container'
                sh "docker run -dt -p ${PORT}:${PORT} --name c001 ${DOCKER_IMAGE}"
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
