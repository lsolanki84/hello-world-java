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
				sudo apt-get update && sudo apt-get install -y nodejs
				sudo apt-get install awscli -y
				sudo apt-get install python3 -y
				sudo apt-get install npm -y 
				sudo apt-get install virtualenv -y
				sudo npm install -g aws-cdk
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

