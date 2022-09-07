pipeline {
    agent any
    environment {
        AWS_ACCOUNT_ID="xxxxxxxxxxx"
        AWS_DEFAULT_REGION="us-east-1"     
    }
    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/tkibnyusuf/Infrastructure_Provisioning.git'
            }
        }
        
        stage('provision eks-cluster') {
           environment {
             AWS_ACCESS_KEY_ID = credentials('aws_access_key_id')
             AWS_SECRET_ACCESS_KEY = credentials('aws_secret_access_key')
           }
           steps {
              script {
                  sh "terraform init"
                  sh "terraform validate"
                  sh "terraform plan"
                  sh " terraform apply --auto-approve"
            }
        }
               
     }
    }
    
}
