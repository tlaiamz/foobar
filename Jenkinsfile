pipeline {
  agent any
  environment {
    AWS_ROLE_ARN = 'arn:aws:iam::461731163182:role/CodeGuruSecurityJenkinsAccessRole'
    AWS_WEB_IDENTITY_TOKEN_FILE = credentials('aws-jwt')
  }
  stages {
    stage('CodeGuru Security') {
      steps {
        sh 'docker run public.ecr.aws/codeguru-security/codegurusecurity-actions-public --source_path . --aws_region us-west-2 --scan_name JENKINS-${JOB_NAME} --output_file_prefix codeguru-security-results --output_file_format SARIF'
      }
    }
  }
}
