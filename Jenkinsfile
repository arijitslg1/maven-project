pipeline {
		agent any {
	
		stages {
			stage ('SCM Checkout')
			{
				git 'https://github.com/arijitslg1/maven-project.git'
				}
			}
			stage ('Testing Stage') {	
			
				steps {
						withMaven(maven : 'LocalMaven') {
						sh 'maven test'
					}		
				}			
			
			}		
	}		

