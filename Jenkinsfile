pipeline {
podTemplate(containers: [
    containerTemplate(
        name: 'jnlp', 
        image: 'lsolanki84/jks-cdk'
        )
  ]) {

    node(POD_LABEL) {
        stage('Get a CDK project') {
            container('jnlp') {
                stage('Shell Execution') {
                    sh '''
		    aws --version
                    echo "Hello! I am executing shell"
                    '''
                }
            }
        }

    }
}
}
