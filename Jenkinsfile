pipeline {
  agent any
  environment {
    AWS_ROLE_ARN = 'arn:aws:iam::461731163182:role/CodeGuruSecurityJenkinsAccessRole'
    AWS_WEB_IDENTITY_TOKEN_FILE = credentials('2dfa4a43-c36f-4c8f-a9ee-e78fd14ea9f9')
  }
  stages {
    stage('CodeGuru Security') {
      steps {
        sh 'aws codeguru-security list-scans'
      }
    }
  }
}
