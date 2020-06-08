pipeline {

  environment {
    ECR_ADDR = "738977827261.dkr.ecr.ap-northeast-1.amazonaws.com"
    REPO = "munics-h5-dev"
    AWS_ACCESS_KEY_ID = credentials('AWS_AK')
    AWS_SECRET_ACCESS_KEY = credentials('AWS_SK')
    DEPLOYMENT_FILE = "nacos-k8s.yaml"
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git(
            url: 'https://github.com/venuszpli/nacos-k8s.git',
            credentialsId: 'gitCredential',
            branch: "master"
        )
      }
    }
    
    stage('Deploy Nacos') {
      steps {
          sh "cd nacos-k8s"
          sh "chmod +x quick-startup.sh"
          sh "./quick-startup.sh"
            }
        }
    }
}
