pipeline {
    	agent { label 'jenkins-mvn'}
	environment {
        PATH=$PATH:/usr/bin/aws:/usr/local/bin/cdk
    }
	stages {
        stage('Build') {
                    steps {
			    script {
				sh "/usr/local/bin/aws --version"
				sh "sleep 3600"
                        }
		    }
        }
    }
}

