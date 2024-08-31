pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                echo 'Maven is specified as the build automation tool.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                echo 'JUnit and Selenium are specified as the test automation tools.'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                echo 'SonarQube is specified as the code analysis tool.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                echo 'OWASP Dependency Check is specified as the security scanning tool.'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to the staging server...'
                echo 'The staging server is specified as an AWS EC2 instance.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                echo 'The same test automation tools (JUnit, Selenium) are used for staging.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to the production server...'
                echo 'The production server is specified as an AWS EC2 instance.'
            }
        }
    }

    post {
        always {
            echo 'Sending email notifications at the end of the Test and Security Scan stages...'
            echo 'Notification emails will include the status of the stage and logs as attachments.'
        }
    }
}
