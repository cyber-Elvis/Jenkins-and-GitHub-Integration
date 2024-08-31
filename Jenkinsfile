pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Task: Build - Using Maven to clean and package the project'
            }
        }
        stage('Test') {
            steps {
                echo 'Task: Test - Using Maven to run tests'
            }
            post {
                success {
                    mail to: 'elvisifeanyi67@gmail.com',
                         subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                         body: "The Test stage of the pipeline has succeeded."
                }
                failure {
                    mail to: 'elvisifeanyi67@gmail.com',
                         subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                         body: "The Test stage of the pipeline has failed. Please check the logs."
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Task: Code Analysis - Using SonarQube for code analysis'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Task: Security Scan - Using OWASP Dependency-Check for security scanning'
            }
            post {
                success {
                    mail to: 'elvisifeanyi67@gmail.com',
                         subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                         body: "The Security Scan stage of the pipeline has succeeded."
                }
                failure {
                    mail to: 'elvisifeanyi67@gmail.com',
                         subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                         body: "The Security Scan stage of the pipeline has failed. Please check the logs."
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Task: Deploy to Staging - Printing deployment instructions'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Task: Integration Tests - Running integration tests on staging environment'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Task: Deploy to Production - Printing production deployment instructions'
            }
        }
    }

    post {
        always {
            mail to: 'elvisifeanyi67@gmail.com',
                 subject: "Pipeline ${currentBuild.fullDisplayName}",
                 body: "The pipeline has ${currentBuild.currentResult}. Please check the logs."
        }
    }
}
