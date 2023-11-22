pipeline {
     agent { label 'jenkins-mvn' }
     tools {
        maven 'testmvn'
    }
    stages {
        stage('Build') {
                    steps {
			    withMaven {
    				sh "mvn clean" 
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

