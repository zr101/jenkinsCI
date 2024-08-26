pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Use Maven for Java projects as an example
                sh 'mvn clean package'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Use JUnit for example
                sh 'mvn test'
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Use SonarQube for example
                sh 'mvn sonar:sonar'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Use OWASP Dependency Check as an example
                sh 'mvn dependency-check:check'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                // Example deploy to AWS EC2
                sh 'scp target/myapp.war user@staging-server:/path/to/deploy'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Example: Using curl to test API endpoints
                sh 'curl -f http://staging-server/api/test-endpoint'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
                // Example deploy to AWS EC2
                sh 'scp target/myapp.war user@production-server:/path/to/deploy'
            }
        }
    }

    post {
        success {
            mail to: 'user@example.com',
                 subject: "Jenkins Pipeline Successful: ${currentBuild.fullDisplayName}",
                 body: "The pipeline has completed successfully."
        }
        failure {
            mail to: 'user@example.com',
                 subject: "Jenkins Pipeline Failed: ${currentBuild.fullDisplayName}",
                 body: "The pipeline has failed. Please check the attached logs.",
                 attachLog: true
        }
    }
}
