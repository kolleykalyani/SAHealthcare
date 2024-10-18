pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/kolleykalyani/health-care-project/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with kalyani'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with kalyani'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with kalyani'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with kalyani'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg1 .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8082:8082 --name c001 myimg1'
            }
        }   
    }
}
