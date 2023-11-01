pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
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
				sleep 5
				docker stop apps
					'''
            }
        }
    }
}