pipeline {
  agent any
  environment {
    AWS_ROLE_ARN = 'arn:aws:iam::461731163182:role/CodeGuruSecurityJenkinsAccessRole'
    AWS_WEB_IDENTITY_TOKEN_FILE = credentials('2dfa4a43-c36f-4c8f-a9ee-e78fd14ea9f9')
  }
  stages {
    stage('CodeGuru Security') {
      steps {
        sh 'docker run \
        -e AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID \
        -e AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY \
        -e AWS_SESSION_TOKEN=$AWS_SESSION_TOKEN \
        public.ecr.aws/codeguru-security/codegurusecurity-actions-public \
        --source_path . \
        --aws_region us-west-2 \
        --scan_name JENKINS-${JOB_NAME} \
        --output_file_prefix codeguru-security-results \
        --output_file_format SARIF'
      }
    }
  }
}
