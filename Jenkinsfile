pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Task: Build - Using Maven to clean and package the project'
                bat 'echo mvn clean package > build.log' // Simulate build log
            }
            post {
                always {
                    emailext to: 'elvisifeanyi67@gmail.com',
                            subject: "Build Stage Notification: ${currentBuild.fullDisplayName}",
                            body: "The Build stage of the pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                            attachLog: true,
                            attachmentsPattern: 'build.log'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Task: Test - Using Maven to run tests'
                bat 'echo mvn test > test.log' // Simulate test log
            }
            post {
                always {
                    emailext to: 'elvisifeanyi67@gmail.com',
                            subject: "Test Stage Notification: ${currentBuild.fullDisplayName}",
                            body: "The Test stage of the pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                            attachLog: true,
                            attachmentsPattern: 'test.log'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Task: Code Analysis - Using SonarQube for code analysis'
                bat 'echo SonarQube analysis > code_analysis.log' // Simulate code analysis log
            }
            post {
                always {
                    emailext to: 'elvisifeanyi67@gmail.com',
                            subject: "Code Analysis Stage Notification: ${currentBuild.fullDisplayName}",
                            body: "The Code Analysis stage of the pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                            attachLog: true,
                            attachmentsPattern: 'code_analysis.log'
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Task: Security Scan - Using OWASP Dependency-Check for security scanning'
                bat 'echo OWASP security scan > security_scan.log' // Simulate security scan log
            }
            post {
                always {
                    emailext to: 'elvisifeanyi67@gmail.com',
                            subject: "Security Scan Stage Notification: ${currentBuild.fullDisplayName}",
                            body: "The Security Scan stage of the pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                            attachLog: true,
                            attachmentsPattern: 'security_scan.log'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Task: Deploy to Staging - Printing deployment instructions'
                bat 'echo Deploying to staging > deploy_staging.log' // Simulate deployment log
            }
            post {
                always {
                    emailext to: 'elvisifeanyi67@gmail.com',
                            subject: "Deploy to Staging Stage Notification: ${currentBuild.fullDisplayName}",
                            body: "The Deploy to Staging stage of the pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                            attachLog: true,
                            attachmentsPattern: 'deploy_staging.log'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Task: Integration Tests - Running integration tests on staging environment'
                bat 'echo Integration tests on staging > integration_tests_staging.log' // Simulate integration tests log
            }
            post {
                always {
                    emailext to: 'elvisifeanyi67@gmail.com',
                            subject: "Integration Tests Stage Notification: ${currentBuild.fullDisplayName}",
                            body: "The Integration Tests stage of the pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                            attachLog: true,
                            attachmentsPattern: 'integration_tests_staging.log'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Task: Deploy to Production - Printing production deployment instructions'
                bat 'echo Deploying to production > deploy_production.log' // Simulate production deployment log
            }
            post {
                always {
                    emailext to: 'elvisifeanyi67@gmail.com',
                            subject: "Deploy to Production Stage Notification: ${currentBuild.fullDisplayName}",
                            body: "The Deploy to Production stage of the pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                            attachLog: true,
                            attachmentsPattern: 'deploy_production.log'
                }
            }
        }
    }

    post {
        always {
            emailext to: 'elvisifeanyi67@gmail.com',
                    subject: "Pipeline Summary: ${currentBuild.fullDisplayName}",
                    body: "The entire pipeline has completed with status: ${currentBuild.currentResult}. Please check the logs.",
                    attachLog: true,
                    attachmentsPattern: '**/*.log' // Attach all generated logs
        }
    }
}
