pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                checkout scm
            }
        }

        stage('Send Email') {
            steps {
                script {
                    def subject = "Readme File from Git Repository"
                    def body = "Please find the attached README file from the Git repository."

                    // Define the recipients
                    def to = "frigui.brahim@esprit.tn"

                    // Attach the README file from the workspace
                    def attachment = [
                        [$class: 'FileAttachment', file: 'README.md', fileName: 'README.md']
                    ]

                    // Send the email
                    emailext (
                        subject: subject,
                        body: body,
                        to: to,
                        attachmentsPattern: 'README.md',
                        mimeType: 'text/plain',
                        attachLog: false
                    )
                }
            }
        }
    }
}
