pipeline {
    	agent { label 'jenkins-mvn'}
	environment {
		PATH = "/usr/bin/aws:/usr/local/bin/cdk:${env.PATH}"
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

