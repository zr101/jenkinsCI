pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo  'Building project to compile and package using Maven.'
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                echo 'JUnit test for code function.'
                echo 'Integration Test working together.'
            }
            // post{ 
            //         success{
            //             mail to: "zaeem.r2021@gmail.com",
            //             subject: "Success: JUnit and Integration test successful.",
            //             body: "Stage is working."
            //         }
            //         failure{
            //             mail to: "zaeem.r2021@gmail.com",
            //             subject: "Unsuccess: JUnit and Integration test failure.",
            //             body: "Stage is not working. Please try to test again."
            //         }
            //     }
        }

        stage("Code Analysis") {
            steps {
                 echo 'Performing code analysis using SonarQube'
            }
        }

        stage("Security Scan") {
            steps {
               echo 'Performing security scan using SonarQube'
            }
             post{ 
                    success{
                        mail to: "zaeem.r2021@gmail.com",
                        subject: "Success: Security scans successful.",
                        body: "Scan is secure."
                    }
                    failure{
                        mail to: "zaeem.r2021@gmail.com",
                        subject: "Unsuccess: Security scans failure.",
                        body: "Scan is not secure. Please try to protect application."
                    }
                }
        }

        stage("Deploy to Staging") {
            steps {
                 echo 'Deploy to staging sever AWS EC2 s3://staging-bucket/'
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo 'Run Integration Tests on Staging environment'
            }
        }

        stage("Deploy to Production") {
            steps {
                echo'Deploy to Production server AWS EC2'
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