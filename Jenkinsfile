import groovy.json.JsonOutput
import groovy.json.JsonSlurper
import java.util.Date
def jobName = currentBuild.fullDisplayName
def mailToRecipients = 'manikandanv@idatalytics.com'
def useremail='manikandan.vensi@gmail.com'
def userAborted = false
pipeline {
  agent any
  stages {
       stage('Build') {
        steps {
           echo "mani"
           
           script {
                emailext body: ''' Please go to console output of ${BUILD_URL}input to approve or Reject.<br> ''',    
                mimeType: 'text/html',
                subject: "[Jenkins] ${jobName} Build Approval Request",
                from: "${useremail}",
                to: "${mailToRecipients}",
                recipientProviders: [[$class: 'CulpritsRecipientProvider']]
                echo "Building1"
                try { 
                    userInput = input submitter: 'manikandanv', message: 'Do you approve?'
                } catch (org.jenkinsci.plugins.workflow.steps.FlowInterruptedException e) {
                cause = e.causes.get(0)
                echo "Aborted by " + cause.getUser().toString()
                userAborted = true
                    echo "SYSTEM aborted, but looks like timeout period didn't complete. Aborting."
                }
                    if (userAborted) {
                currentBuild.result = 'ABORTED'
                } else {
                echo "Building2"
                }


            }
        }
      
       }     
    }

}





 
