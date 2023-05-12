pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
                // Perform the build steps here
            }
            post {
                always  {
                    sendEmailNotification('Build')
                }
            }
        }

        // Other stages follow the same pattern

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to a production server (e.g., AWS EC2)'
                // Perform the deployment steps here
            }
            post {
                always {
                    sendEmailNotification('Deploy to Production')
                }
            }
        }
    }
}

def sendEmailNotification(stageName) {
    mail to: "josh.kilinc@gmail.com",
    subject: "Pipeline ${currentBuild.result}: ${stageName}",
    body: """
        Stage: ${stageName}
        Status: ${currentBuild.result}
        """,
    attachmentsPattern: 'build.log'
}
