pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
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
                sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'dependency-check.sh --project Github integration -e --scan ./'
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
                sh 'scp target/my-app.jar cyber-elvis@staging-server-address:/actual/path/to/deploy/'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                sh 'mvn verify -Denv=staging'
            }
        }
        stage('Deploy to Production') {
            steps {
                sh 'scp target/my-app.jar cyber-elvis@production-server-address:/actual/path/to/deploy/'
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
