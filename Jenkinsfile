pipeline {
    	agent { label 'jenkins-mvn'}
	environment {
        PATH = "${tool 'AWS-CLI'}:${env.PATH}"
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

