pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo 'Building project to compile and package using Maven.'
            }
        } // made changes

        stage("Unit and Integration Tests") {
            steps {
                echo 'Running JUnit tests and Integration Tests.'
            }
            post { 
                success {
                    emailext(
                        to: "zaeem.r2021@gmail.com",
                        subject: "SUCCESS: Unit and Integration Tests Passed",
                        body: "The Unit and Integration tests have passed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "zaeem.r2021@gmail.com",
                        subject: "FAILURE: Unit and Integration Tests Failed",
                        body: "The Unit and Integration tests have failed. Please check the logs.",
                        attachLog: true
                    )
                }
            }
        }

        stage("Code Analysis") {
            steps {
                echo 'Performing code analysis using SonarQube.'
            }
        }

        stage("Security Scan") {
            steps {
                echo 'Performing security scan using SonarQube.'
            }
            post { 
                success {
                    emailext(
                        to: "zaeem.r2021@gmail.com",
                        subject: "SUCCESS: Security Scan Passed",
                        body: "The security scan has passed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "zaeem.r2021@gmail.com",
                        subject: "FAILURE: Security Scan Failed",
                        body: "The security scan has failed. Please check the logs.",
                        attachLog: true
                    )
                }
            }
        }

        stage("Deploy to Staging") {
            steps {
                echo 'Deploying to staging server AWS EC2.'
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo 'Running Integration Tests on Staging environment.'
            }
        }

        stage("Deploy to Production") {
            steps {
                echo 'Deploying to Production server AWS EC2.'
            }
        }
    }

    post {
        success {
            echo 'Deployment to production successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
