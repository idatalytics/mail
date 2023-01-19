pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'mani'
        script {
          approval(approver: 'john.doe', timeout: 30)

          emailext(
            to: 'john.doe@example.com',
            subject: "Approval needed for Jenkins Pipeline Build: ${currentBuild.fullDisplayName}",
            body: "Please approve the Jenkins Pipeline Build ${currentBuild.fullDisplayName} by clicking ${currentBuild.url}.",
            trigger: "always"
          )
        }

      }
    }

  }
}