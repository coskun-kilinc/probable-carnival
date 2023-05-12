pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
            }
            post {
                always {
                    emailext attachLog: true, attachmentsPattern: 'build.txt',
                    mail to: "josh.kilinc@gmail.com",
                    subject: "Build Status: ${currentBuild.result}",
                    body: "Build log attached!",
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests'
                echo 'Running integration tests'
            }
            post {
                always {
                    mail to: "josh.kilinc@gmail.com",
                    subject: "Unit and Integration Test Status Email",
                    body: "Unit and Integration Test log attached!"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code using a code analysis tool (e.g., SonarQube)'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing a security scan using a security scanning tool (e.g., SonarQube or OWASP ZAP)'
            }
            post {
                always {
                    mail to: "josh.kilinc@gmail.com",
                    subject: "Security Scan Status Email",
                    body: "Security Scan log attached!"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to a staging server (e.g., AWS EC2)'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to a production server (e.g., AWS EC2)'
            }
        }
    }
}
