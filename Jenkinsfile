def uuid = UUID.randomUUID().toString()

properties([parameters([string(defaultValue: 'us-east-1', description: 'AWS DEFAULT REGION', name: 'AWS_DEFAULT_REGION', trim: false)])])

pipeline {
  agent any
  stages {
      stage('Provision EC2 server') {
        steps {
          withCredentials([string(credentialsId: 'AWSAccessID', variable: 'AWS_ACCESS_KEY_ID')]) {
            withCredentials([string(credentialsId: 'AWS Secret', variable: 'AWS_SECRET_ACCESS_KEY')]) {
              sh 'aws cloudformation create-stack --stack-name cfn-ec2-${uuid} --template-body file://./cf-ec2-redhat-appserver0.template'
            }
          }
        }
      }
    }
}
