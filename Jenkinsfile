pipeline {
      agent any
      stages {
        stage('Hello') {
	          steps {
		          echo 'Hello world'
	           }
		}
	      
	      stage('Checkout GIT ') {
            steps {
                echo 'Pulliing ...';
		    git branch: 'master', url: 'https://github.com/mhassini/avec-maven.git'
            }
        }
	      
	      
	stage('Testing maven') {
		steps {
		sh """mvn -version"""
	      }
	}
	stage('Scan') {
		steps {
		withSonarQubeEnv(installationName: 'sq1') {
		sh """mvn clean org.sonarsource.scanner.maven:sonar-maven-plugin:8.9.7-community:sonar"""
	      }
	}
	}
}
}
