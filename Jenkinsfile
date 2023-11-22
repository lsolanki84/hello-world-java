pipeline {
     agent { label 'jenkins-mvn' }
     tools {
        maven 'Maven 3.8.7'
        jdk 'Java 17.0.9'
    }	
    stages {
        stage('Build') { 
            steps {
                sh '''
		export M2_HOME=/usr/share/maven
		export PATH=$PATH:$M2_HOME/bin
  		export MAVEN_HOME=/usr/share/maven
		export PATH=$PATH:$MAVEN_HOME/bin
		mvn --version
		'''
		sh "mvn clean" 
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test package" 
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
