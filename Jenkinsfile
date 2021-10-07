pipeline {
  agent {
    docker {
      image 'hashicorp/terraform:1.0.8'
    }
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

