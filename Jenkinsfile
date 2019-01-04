def uuid = UUID.randomUUID().toString()

pipeline {
  agent any
  stages {
      stage('Provision EC2 server') {
        steps {
          sh 'aws cloudformation create-stack --stack-name cfn-ec2-${uuid} --template-body file://./cf-ec2-redhat-appserver0.template'
        }
      }
    }
}
