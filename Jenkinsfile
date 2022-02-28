pipeline {
    agent any
    environment {
        committerEmail = sh (
         script: 'git --no-pager show -s --format=\'%ae\'',
         returnStdout: true
         ).trim()
    }
    stages {
        stage('git') {
            steps {
             git 'https://github.com/Ankit-9575/new11.git'
        }
    }
    }
     post {
        success {
         
            emailext to: committerEmail, body: [[${BUILD_LOG}]], subject: 'SUCCESS: ${currentBuild.fullDisplayName}', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            
        }
}
}
