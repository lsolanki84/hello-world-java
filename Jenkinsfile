podTemplate(containers: [
    containerTemplate(
        name: 'maven', 
        image: 'maven:latest', 
        command: 'sleep', 
        args: '30d'
        ),
  ]) {

    node(POD_LABEL) {
        stage('Get a Maven project') {
            git 'https://github.com/lsolanki84/hello-world-java.git'
            container('maven') {
                stage('Build a Maven project') {
                    sh '''
                    mvn clean
                    mvn test
                    mvn package
                    '''
                }
            }
        }

    }
}
