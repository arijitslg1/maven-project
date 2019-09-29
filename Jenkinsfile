pipeline {
	agent any {
	
		stages {
			stage "SCM Checkout"
			{
				git 'https://github.com/arijitslg1/maven-project.git'
				}
			}
		stage "code test"	
			withMaven(maven: 'LocalMaven') {
				sh 'maven test'
			}			
			
		}		
}
