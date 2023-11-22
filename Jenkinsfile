pipeline {
     agent { label 'jenkins-mvn' }
     tools {
        maven 'testmvn'
        jdk 'DefaultJDK'
    }	
    stages {
        stage('Build') {
                    steps {
			    withMaven(globalMavenSettingsConfig: '', jdk: '', maven: '', mavenSettingsConfig: '', traceability: true) {
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
				                docker build -t appimage .
				                docker stop apps
				                docker rm -f apps
				                docker run -d --name apps -p 8282:8080 appimage
				                sleep 15
				                docker stop apps
					            '''
                        }
	    }
    }
}  

