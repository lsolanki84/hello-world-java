pipeline {
     agent 'jenkins-mvn'
     tools {
        maven 'testmvn'
	jdk 'testjdk'
    }
    stages {
        stage('Build') {
                    steps {
			    script {
				sh "env"    
			   /* sh "export PATH=$PATH:/usr/bin/aws:/usr/local/bin/cdk" */
			    sh "/usr/bin/aws --version"
			    sh "/usr/local/bin/cdk --version"
			    withMaven {
    				sh "mvn clean" 
			    }
                        }
		    }
        }
        stage('Test') { 
                    steps {
		                    withMaven { sh "mvn test package" 
                            }
                        }
        }
        stage('Deploy') { 
			        steps {
                            sh ''' 
				echo "Deploying app..."
				sleep 5
				echo "Deployment done"
				 '''
                        }
	    }
    }
}  
