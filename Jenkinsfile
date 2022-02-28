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
         
            emailext to: committerEmail, body:  '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:$BUILD_LOG maxLines=8000, escapeHtml=true', subject: 'SUCCESS: $jenkins-${JOB_NAME}-${BUILD_NUMBER}', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            
        }
}
}
