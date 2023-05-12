pipeline {
    agent any

    environment {
		emailAddress  = "josh.kilinc@gmail.com"


	}


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
    emailext attachLog: true, body: "${currentBuild.result}: ${stageName}", compressLog: true, replyTo: "${emailAddress}",
       subject: "Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", to: "${emailAddress}"
        // mail to: "josh.kilinc@gmail.com",
        // emailext subject: "Pipeline ${currentBuild.result}: ${stageName}",
        //     body: """
        //         Stage: ${stageName}
        //         Status: ${currentBuild.result}
        //         ${BUILD_LOG, maxLines, escapeHtml}
        //         """,
        //     attachmentsPattern: 'build.log'
}
