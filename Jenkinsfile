import groovy.json.JsonOutput
import groovy.json.JsonSlurper
import java.util.Date

pipeline {
  agent any
  stages {
       stage('Build') {
        steps {
            def jobName = currentBuild.fullDisplayName
            def mailToRecipients = 'manikandanv@idatalytics.com'
            def useremail='manikandanv@idatalytics.com'
            def userAborted = false
            script {
                emailext body: ''' Please go to console output of ${BUILD_URL}input to approve or Reject.<br> ''',    
                mimeType: 'text/html',
                subject: "[Jenkins] ${jobName} Build Approval Request",
                from: "${useremail}",
                to: "${mailToRecipients}",
                recipientProviders: [[$class: 'CulpritsRecipientProvider']]


            }
        }
      
       }     
    }

}
