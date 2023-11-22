pipeline {
     agent { label 'jenkins-mvn' }
     tools {
        maven 'DefaultMVN'
        jdk 'DefaultJDK'
    }	
    stages {
        stage('Build') { 
            steps {
		sh "echo $JAVA_HOME"
  		sh "echo $M2_HOME"
		sh "echo $MAVEN_HOME"
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
