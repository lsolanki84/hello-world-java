podTemplate(containers: [
    containerTemplate(
        name: 'jnlp', 
        image: 'ubuntu:latest'
        )
  ]) {

    node(POD_LABEL) {
        stage('Get a CDK project') {
            container('jnlp') {
                stage('Shell Execution') {
                    sh '''
                    echo "Hello! I am executing shell"
                    '''
                }
            }
        }

    }
}

