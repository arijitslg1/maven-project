pipeline {
    agent any	
    stages {
	    stage ('SCM Checkout') {
	    steps {	
	       git url: "https://github.com/arijitslg1/maven-project"
	 }
	}
	
	stage ('Compile Stage') {
            steps {
                withMaven(jdk: 'localjdk-1.8', maven: 'localmaven') 
                {   
                    sh 'mvn compile' 
                }
               }
              }
	
	
	stage ('Testing Stage') {
	    steps {
		withMaven(jdk: 'localjdk-1.8', maven : 'LocalMaven') 
		{		
		    sh 'mvn test'
		}				
	       }		
	      }							
	
	stage ('Testing Installation') {
	   steps {
		withMaven(jdk: 'localjdk-1.8', maven : 'LocalMaven') 
		{
                    sh 'mvn package'
                }                                 
              }
            }

    }      
}
