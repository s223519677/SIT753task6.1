pipeline {
    agent any
    environment {
        branch = 'main'
        scmUrl = 'https://github.com/s223519677/SIT753task6.1.git'
        serverPort = '8080'
        stagingServer = 'http://ec2-16-171-29-48.eu-north-1.compute.amazonaws.com:8080'
        productionServer = 'http://ec2-16-171-29-48.eu-north-1.compute.amazonaws.com:8080'
    }
    stages {
        stage('checkout git') {
            steps {
                git branch: branch, credentialsId: 'https', url: scmUrl
                 echo "Fetching source code from github"
            }
        }

        stage('build') {
            steps {
                
                echo "Maven Compiling code and generating artifacts"
            }
        }

        stage ('Unit & Intergration Test') {
            steps {
                parallel (
                    "unit tests": { powershell 'mvn test' },
                    "integration tests": { powershell 'mvn integration-test' }
                )
            }
        }

        stage('deploy to Production'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://ec2-16-171-29-48.eu-north-1.compute.amazonaws.com:8080')], contextPath: 'null',  war: 'target/*.war'
                 echo "Deploying Code to AWS EC2"
                  echo "Access the ec2 http://ec2-16-171-29-48.eu-north-1.compute.amazonaws.com:8080/manager/html "
            }
        }
        stage('deploy to staging(Test'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://ec2-16-171-29-48.eu-north-1.compute.amazonaws.com:8080')], contextPath: 'testapp',  war: 'target/*.war'
                 echo "Deploying Code to AWS EC2"
            }
        }

       // stage('deploy staging'){
       //     steps {
        //        deploy(stagingServer, serverPort)
        //    }
        //}

       // stage('deploy production'){
         //   steps {
         //       deploy(productionServer, serverPort)
         //   }
        //}
    }
    post {
        success {
            mail to: 'okoraforokechukwu@gmail.com', subject: 'Pipeline Success', body: "${env.BUILD_URL}"
         echo "Sending Pipeline E-mail to Senior Software engineer paul"  
        }
    }
}
