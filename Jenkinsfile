podTemplate(containers: [
    containerTemplate(
        name: 'maven', 
        image: 'awscdk/cdk', 
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
