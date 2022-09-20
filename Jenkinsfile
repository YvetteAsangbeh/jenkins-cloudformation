pipeline {
    agent any
    stages {
        stage('Validate Stack') {
            steps {
            sh "aws cloudformation validate-template --template-body file://ventura-network-infra.yaml --region 'us-east-1'"
            }
        }
        stage('Template Cost Estimate') {
            steps {
            sh "aws cloudformation estimate-template-cost --template-body file://ventura-network-infra.yaml --region 'us-east-1'"
            }
        }
        stage('Create Stack') {
            steps {
            sh "aws cloudformation create-stack --stack-name s3bucket --template-body file://ventura-network-infra.yaml --region 'us-east-1'"
            }
        }
        //stage('Slack Notification'){
        //    slackSend baseUrl: 'https://hooks.slack.com/services/',
        //    channel: '#jenkins-pipeline-demo',
        //    color: 'good', 
        //    message: 'Welcome to Jenkins, Slack!', 
        //    teamDomain: 'javahomecloud',
        //    tokenCredentialId: 'slack-demo'
        //}
    }
}