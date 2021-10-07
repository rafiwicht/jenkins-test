pipeline {
  agent {
    docker {
      image 'jenkins-terraform-agent:latest'
    }
  }
  environment {
      AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
      AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
  }
  stages {
    stage('Init') {
      steps {
        sh 'terraform init'
      }
    }
    stage('Plan') {
      steps {
        sh 'terraform plan -out apply.plan'
      }
    }
    stage('Apply') {
      steps {
        sh 'terraform apply -auto-approve apply.plan'
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}

