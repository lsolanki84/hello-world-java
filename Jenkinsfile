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
                stage('Build a CDK project') {
                    sh '''
                    cdk --version
                    aws --version
                    '''
                }
            }
        }

    }
}
