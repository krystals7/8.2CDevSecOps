pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build – Build the code using a build automation tool to compile and package your code. Tool: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests – Run unit tests to ensure the code functions as expected and run integration tests to ensure the different components of the application work together as expected. Tools: JUnit + TestNG'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis – Analyse the code and ensure it meets industry standards. Tool: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan – Perform a security scan on the code to identify any vulnerabilities. Tool: OWASP Dependency-Check'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging – Deploy the application to a staging server (e.g., AWS EC2 instance). Tool: AWS EC2'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging – Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment. Tool: Selenium'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production – Deploy the application to a production server (e.g., AWS EC2 instance). Tool: AWS EC2'
            }
        }
    }
}
