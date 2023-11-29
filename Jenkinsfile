pipeline {
    	agent { label 'jenkins-mvn'}
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

