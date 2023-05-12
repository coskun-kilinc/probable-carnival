pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
                // Perform the build steps here
            }
            post {
                success {
                    sendEmailNotification('Build', true)
                }
                failure {
                    sendEmailNotification('Build', false)
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
                success {
                    sendEmailNotification('Deploy to Production', true)
                }
                failure {
                    sendEmailNotification('Deploy to Production', false)
                }
            }
        }
    }
}

def sendEmailNotification(stageName, isSuccessful) {
    emailext subject: "Pipeline ${currentBuild.result}: ${stageName}",
        body: """
            <p>Stage: ${stageName}</p>
            <p>Status: ${isSuccessful ? 'Success' : 'Failure'}</p>
            """,
        attachmentsPattern: 'build.log'
}
