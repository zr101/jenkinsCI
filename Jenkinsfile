pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo 'Building project to compile and package using Maven.'
                sh 'mvn clean package'
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                echo 'Running JUnit tests to ensure code functions as expected.'
                sh 'mvn test'
                echo 'Running Integration Tests to ensure components work together.'
                // Add your integration test commands here
            }
            post { 
                success {
                    mail to: "zaeem.r2021@gmail.com",
                    subject: "Success: JUnit and Integration tests successful.",
                    body: "The Unit and Integration Tests stage completed successfully."
                }
                failure {
                    mail to: "zaeem.r2021@gmail.com",
                    subject: "Failure: JUnit and Integration tests failed.",
                    body: "The Unit and Integration Tests stage failed. Please review the logs and fix the issues."
                }
            }
        }

        stage("Code Analysis") {
            steps {
                echo 'Performing code analysis using SonarQube.'
                sh 'mvn sonar:sonar'
            }
        }

        stage("Security Scan") {
            steps {
                echo 'Performing security scan using OWASP Dependency Check.'
                sh 'mvn dependency-check:check'
            }
            post { 
                success {
                    mail to: "zaeem.r2021@gmail.com",
                    subject: "Success: Security scan successful.",
                    body: "The Security Scan stage completed successfully."
                }
                failure {
                    mail to: "zaeem.r2021@gmail.com",
                    subject: "Failure: Security scan failed.",
                    body: "The Security Scan stage failed. Please review the logs and address any vulnerabilities."
                }
            }
        }

        stage("Deploy to Staging") {
            steps {
                echo 'Deploying to staging server on AWS EC2 (s3://staging-bucket/).'
                // Replace with actual deployment command
                sh 'scp target/myapp.war user@staging-server:/path/to/deploy'
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo 'Running Integration Tests on Staging environment.'
                // Add your staging integration test commands here
                sh 'curl -f http://staging-server/api/test-endpoint'
            }
        }

        stage("Deploy to Production") {
            steps {
                echo 'Deploying to Production server on AWS EC2.'
                // Replace with actual production deployment command
                sh 'scp target/myapp.war user@production-server:/path/to/deploy'
            }
        }
    }

    post {
        success {
            echo 'Deployment to production successful!'
            mail to: "zaeem.r2021@gmail.com",
                 subject: "Success: Production deployment successful.",
                 body: "The deployment to production completed successfully."
        }
        failure {
            echo 'Deployment failed!'
            mail to: "zaeem.r2021@gmail.com",
                 subject: "Failure: Deployment failed.",
                 body: "The deployment process failed. Please check the logs and resolve the issues."
        }
    }
}
