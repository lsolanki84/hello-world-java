pipeline {
     agent { label 'jenkins-mvn' }
     tools {
        maven 'testmvn'
	jdk 'testjdk'
    }
    stages {
        stage('Build') {
                    steps {
			    sh '''
				apt-get update && apt-get install -y nodejs
				apt-get install awscli -y
				apt-get install python3 -y
				apt-get install npm -y 
				apt-get install virtualenv -y
				npm install -g aws-cdk
       '''
			    sh "/usr/bin/aws --version"
			    sh "/usr/local/bin/cdk --version"
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

