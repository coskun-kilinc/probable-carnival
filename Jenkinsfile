pipeline {
    agent any

    environment {
            emailAddress  = "josh.kilinc@gmail.com"
        }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests'
                echo 'Running integration tests'
            }
            always  {
                    sendEmailNotification('Unit and Integration Tests')
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
            always  {
                    sendEmailNotification('Security Scan')
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
            always  {
                    sendEmailNotification('Integration Tests on Staging')
                }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to a production server (e.g., AWS EC2)'
            }
        }
    }
}


def sendEmailNotification(stageName) {
        emailext body: "Pipeline ${currentBuild.result}: Job ${env.JOB_NAME} Build #${env.BUILD_NUMBER}\n\n${env.BUILD_URL}",
        mimeType: 'text/html',
        subject: "${currentBuild.result}: ${env.JOB_NAME} build #${env.BUILD_NUMBER}",
        to: "${emailAddress}",
        attachLog: true


        // mail to: "josh.kilinc@gmail.com",
        // subject: "Pipeline ${currentBuild.result}: ${stageName}",
        // body: """
        //     Stage: ${stageName}
        //     Status: ${currentBuild.result}
        //     ${BUILD_LOG, maxLines, escapeHtml}
        //     """,
        // attachmentsPattern: 'build.log'
}
