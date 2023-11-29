pipeline {
    	agent { lable 'jenkins-mvn'}
	stages {
        stage('Build') {
                    steps {
			    script {
				sh "env"
				sh "sleep 3600"    
			    sh "/usr/bin/aws --version"
			    sh "/usr/local/bin/cdk --version"
                        }
		    }
        }
    }
}

