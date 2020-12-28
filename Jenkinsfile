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
                withMaven(jdk: 'LocalJDK', maven: 'LocalMaven') 
                {   
                    sh 'mvn compile' 
                }
               }
              }
	
	
	stage ('Testing Stage') {
	    steps {
		withMaven(jdk: 'LocalJDK', maven : 'LocalMaven') 
		{		
		    sh 'mvn test'
		}				
	       }		
	      }							
	
	stage ('Testing Installation') {
	   steps {
		withMaven(jdk: 'LocalJDK', maven : 'LocalMaven') 
		{
                    sh 'mvn install'
                }                                 
              }
            }
  
	stage ('Deploy-to-Tomcat-Dev') {
	   steps {
		sshagent(['8ba058c6-d4c2-4930-8af9-6d7f899d60bc']) {
                sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.21.251:/var/lib/tomcat/webapps'
                }
	      }
	    }
    }      
}
