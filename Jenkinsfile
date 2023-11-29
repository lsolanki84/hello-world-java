pipeline {
    	agent { label 'jenkins-mvn'}
	stages {
        stage('Build') {
                    steps {
			    script {
				sh '''
				curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
				unzip awscliv2.zip
				sudo ./aws/install
				'''
				sh "aws --version"
                        }
		    }
        }
    }
}

