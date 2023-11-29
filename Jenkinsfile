podTemplate(containers: [
    containerTemplate(
        name: 'maven', 
        image: 'lsolanki84/ub-cdk',        
        command: 'sleep', 
        args: '30d'
        
        ),
  ]) {

    node(POD_LABEL) {
        stage('Get a Maven project') {
            container('maven') {
                stage('Build a Maven project') {
                    sh '''
                    cdk --version
                    aws --version
                    '''
                }
            }
        }

    }
}
