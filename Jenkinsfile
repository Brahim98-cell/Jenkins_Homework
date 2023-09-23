pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Debug Workspace') {
    steps {
        sh 'ls -al ${WORKSPACE}'
    }
}

        stage('Send Email') {
            steps {
                emailext (
                    subject: 'Nouveau commit sur GitHub',
                    body: '''Un nouveau commit a été effectué sur GitHub.
                    Voici le contenu du fichier README.md :

                    ${currentBuild.getWorkspace().child('README.md').read()}

                    Commit URL : ${BUILD_URL}
                    ''',
                    to: 'frigui.brahim@esprit.tn',
                )
            }
        }
    }
}
