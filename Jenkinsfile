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
                    echo 'Running unit tests using JUnit for unit testing and Selenium for integration testing to validate individual components and ensure components work together as expected.'
                }
            }
            post {
                always {
                    emailext (
                        subject: "Jenkins Notification: Unit and Integration Tests Completed",
                        body: "Unit and Integration Tests Stage completed with status: ${currentBuild.currentResult}.",
                        to: 'faizanraza3695@gmail.com'
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing code quality and standards compliance using SonarQube, integrated with Jenkins for automated code review.'
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
                        body: "Security Scan Stage completed with status: ${currentBuild.currentResult}.",
                        to: 'faizanraza3695@gmail.com'
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying the application to a staging environment on AWS EC2 to simulate production conditions using Terraform for infrastructure provisioning.'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running additional integration tests in the staging environment to ensure the application operates as expected under near-production settings using Postman for API testing.'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying the application to the production server on AWS EC2 to make the application live for end-users, using Docker for containerization and Kubernetes for orchestration.'
                }
            }
        }
    }

}
