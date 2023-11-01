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
                sh "docker build -t appimage .;"
				sh "docker stop apps;"
				sh "docker rm -f apps;"
				sh "docker run -d --name apps -p 8282:8080 appimage;" 
            }
        }
    }
}