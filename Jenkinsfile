pipeline {
    agent any
    
        //Maven - Build
        //JUnit - Testing
        //SonarLint - Analysis
        //Appscan - Security
        //Tools
        //Test for github task

    stages {
        stage('Build') {
            steps {
                echo "Run maven"
                echo "Log maven results"
                echo "Archive .jar file"
            }
            }
        stage('Unit and Integration Tests')
        {
            steps {
                echo "Run/build program with unit tests including overflows via JUnit"
                echo "Run/build program with integration tests via JUnit"
                echo "Log results"
            }
            post{
                always{
                    emailext to: "scarlet.easgle@gmail.com",
                    subject: "UI Test Status",
                    body: "${currentBuild.currentResult}",
                    attachLog: true
                }
            }
        }
        stage('Code Analysis')
        {
            steps {
                echo "Run SolarLint on source file"
                echo "Log results"
            }
        }
        stage('Security Scan')
        {
            steps {
                echo "Run Appscan on source file"
                echo "Log Results"
            }
            post {
                always{
                        emailext to: "scarlet.easgle@gmail.com",
                        subject: "Security Test Status",
                        body: "${currentBuild.currentResult}",
                        attachLog: true
                    }
            }
        }
        stage('Deploy to Staging')
        {
            steps {
                echo "Deploy and configure program for staging enviroment: AWS EC2 Stage"
            }
        }
        stage("Integration Tests on Staging")
        {
            steps {
                echo "Run/build program with integration tests via JUnit"
            }
            post {
                always{
                        emailext to: "scarlet.easgle@gmail.com",
                        subject: "Staging UI Test Status",
                        body: "${currentBuild.currentResult}",
                        attachLog: true
                    }
            }
        }
        stage("Deploy to Production"){
            steps {
                echo "Deploy and configure program for production server: AWS EC2 Prod"
            }
        }
    }
}
