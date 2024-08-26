pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
        }
        // stage('Code Analysis') {
        //     steps {
        //         echo 'Performing code analysis...'
        //         sh 'mvn sonar:sonar'
        //     }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                sh 'mvn dependency-check:check'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                sh 'scp target/myapp.war user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                sh 'curl -f http://staging-server/api/test-endpoint'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
                sh 'scp target/myapp.war user@production-server:/path/to/deploy'
            }
        }
    }

    // post {
    //     success {
    //         mail to: 'zaeem.r2021@gmail.com',
    //              subject: "Jenkins Pipeline Successful: ${currentBuild.fullDisplayName}",
    //              body: "The pipeline has completed successfully. \n\nCheck the full logs at: ${env.BUILD_URL}console"
    //     }
    //     failure {
    //         mail to: 'zaeem.r2021@gmail.com.com',
    //              subject: "Jenkins Pipeline Failed: ${currentBuild.fullDisplayName}",
    //              body: "The pipeline has failed. Please check the logs at: ${env.BUILD_URL}console"
    //     }
    // }

