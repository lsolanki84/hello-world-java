podTemplate(containers: [
    containerTemplate(
        name: 'cdk-agent', 
        image: 'lsolanki84/jkin-cdk',        
        command: 'sleep', 
        args: '30d'
        
        ),
  ]) {

    node(POD_LABEL) {
        stage('Project enviroment setup') {
            container('cdk-agent') {

                stage('Assume Role') {
                    
                script {                
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
        stage('Configure AWS') {
                script {
                    // Use the assumed role credentials in your AWS CLI or other AWS-related commands
                    sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"
                    sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
                    sh "aws configure set aws_session_token $AWS_SESSION_TOKEN"
                    sh "aws configure set default.region ap-south-1"
                }
        }

               stage('Build CDK Template') {
                git url: 'https://github.com/lsolanki84/testcdk.git', branch: 'main'
            
                    sh '''
                    ls -lrth
                    aws sts get-caller-identity

                    python3 --version

                    npm --version

                    virtualenv --version

                    cdk --version
                    
                    mkdir s3-project
                    cd s3-project
                    cdk init app --language typescript
                    ls -lrth

                    cp ../s3code lib/s3-project-stack.tc 
                    cat lib/s3-project-stack.tc
                    cdk bootstrap
                    cdk deploy --require-approval never

                    '''
                }
            
                 
    }
}
}
}
