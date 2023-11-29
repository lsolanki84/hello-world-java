pipeline {
    	agent { label 'jenkins-mvn'}
	stages {
        stage('Build') {
                    steps {
			    script {
				sh "env"
				sh "aws --version"    
				sh "sleep 3600"    
			    sh "/usr/bin/aws --version"
			    sh "/usr/local/bin/cdk --version"
                        }
		    }
        }
    }
}

