pipeline {
     agent { node { label 'jenkins-mvn'}
    stages {
        stage('Build') {
                    steps {
			    script {
				sh "env"    
			    sh "/usr/bin/aws --version"
			    sh "/usr/local/bin/cdk --version"
                        }
		    }
        }
    }
}
}
