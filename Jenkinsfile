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
            git branch: 'stage', url: 'https://github.com/Ankit-9575/new11.git'
                sh 'echo "this is from stage branch"'
        }
    }
    }
     post {
        success {
         
            emailext to: committerEmail, body:  'Check console output at $BUILD_URL to view the results. $PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:$BUILD_LOG maxLines=8000, escapeHtml=true ', subject: 'SUCCESS: ${JOB_NAME}-${BUILD_NUMBER} is Successful', recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            
        }
}
}
