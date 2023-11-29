pipeline {
    /* agent { node { label 'jenkins-mvn'}} */
       agent { docker { image 'lsolanki84/jks-mvn' } }
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

