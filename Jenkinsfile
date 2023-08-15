pipeline {
  agent {
    docker {
      image 'node:lts-bullseye-slim'
    }
  }
  stages {
    stage('CodeGuru Security') {
      steps {
        sh 'docker run public.ecr.aws/codeguru-security/codegurusecurity-actions-public --source_path . --aws_region us-west-2 --scan_name JENKINS-${JOB_NAME} --output_file_prefix codeguru-security-results --output_file_format SARIF'
      }
    }
  }
}
