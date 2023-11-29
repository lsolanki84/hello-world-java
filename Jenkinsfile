pipeline {
    	agent { label 'jenkins-mvn'}
	stages {
        stage('Build') {
                    steps {
			    script {
				sh "aws --version"
				sh "sleep 3600"
                        }
		    }
        }
    }
}

