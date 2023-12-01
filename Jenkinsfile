podTemplate(containers: [
    containerTemplate(
        name: 'cdk-agent', 
        image: 'lsolanki84/jkin-cdk',        
        command: 'sleep', 
        args: '30d'
        
        ),
  ]) {

    node(POD_LABEL) {
        stage('Get a CDK project') {
            container('cdk-agent') {

                stage('Assume Role') {
                    
                script {
                    environment {
                        AWS_ROLE_ARN = 'arn:aws:iam::082008957495:role/awstests3fullaccess'
                    }
                        sh "echo ${env.AWS_ROLE_ARN}"
                    
                    // Use Jenkins credentials for AWS CLI
                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'AWS_CREDENTIALS_ID']]) {
                        // Assume the role
                        
                        sh "aws sts assume-role --role-arn arn:aws:iam::082008957495:role/awstests3fullaccess --role-session-name JenkinsSession > assumed-role.json"
                        
                        // Extract temporary credentials from the response
                        AWS_ACCESS_KEY_ID = sh(script: "jq -r '.Credentials.AccessKeyId' assumed-role.json", returnStdout: true).trim()
                        AWS_SECRET_ACCESS_KEY = sh(script: "jq -r '.Credentials.SecretAccessKey' assumed-role.json", returnStdout: true).trim()
                        AWS_SESSION_TOKEN = sh(script: "jq -r '.Credentials.SessionToken' assumed-role.json", returnStdout: true).trim()
                    }
                
            }
        }

        // Your other pipeline stages go here
        stage('test Stage') {
                script {
                    // Use the assumed role credentials in your AWS CLI or other AWS-related commands
                    sh "aws configure set aws_access_key_id ${env.AWS_ACCESS_KEY_ID}"
                    sh "aws configure set aws_secret_access_key ${env.AWS_SECRET_ACCESS_KEY}"
                    sh "aws configure set aws_session_token ${env.AWS_SESSION_TOKEN}"
                    sh "aws s3 ls"
                }
        }
    }
}
}
}
