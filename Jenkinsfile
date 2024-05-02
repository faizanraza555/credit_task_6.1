pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the application using Maven, which automates the project’s build process.'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit tests using JUnit to validate individual components and integration tests to ensure components work together as expected.'
                }
            }
            post {
                always {
                    emailext (
                        subject: "Jenkins Notification: Unit and Integration Tests Completed",
                        body: "Unit and Integration Tests Stage completed with status: ${currentBuild.currentResult}",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing code quality and standards compliance using SonarQube integrated with Jenkins for automated code review.'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scanning using OWASP ZAP to detect vulnerabilities in the application code.'
                }
            }
            post {
                always {
                    emailext (
                        subject: "Jenkins Notification: Security Scan Completed",
                        body: "Security Scan Stage completed with status: ${currentBuild.currentResult}",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying the application to a staging environment on AWS EC2 to simulate production conditions.'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running additional integration tests in the staging environment to ensure the application operates as expected under near-production settings.'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying the application to the production server on AWS EC2 to make the application live for end-users.'
                }
            }
        }
    }
}
