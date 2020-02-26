pipeline {
	agent any	
		stages
			{
			stage ('SCM Checkout')
					{	
						git 'https://github.com/arijitslg1/maven-project.git'
					}
			}
			{
			stage ('Testing Stage') 
					{	
						steps 	{
								withMaven(maven : 'LocalMaven') 
									{		
										sh 'mvn test'
									}				
								}		
				}							
			}
			{
			stage ('Testing Package') 
					{	
						steps 	{
								withMaven(maven : 'LocalMaven') 
									{		
										sh 'mvn package'
									}				
								}		
					}							
			}
			{
			stage ('Testing Installation') 
					{	
						steps 	{
								withMaven(maven : 'LocalMaven') 
									{		
										sh 'mvn install'
									}				
								}		
					}							
			}
			{
			stage ('Testing Deployment to Tomcat') 
					{	
						steps{
								sshagent(['bcc635a1-e80d-4622-9d15-a6d9329b908e']) {
								sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.43.212:/opt/apache-tomcat-9.0.31/webapps'
								}		
							}
					}
				}
			}
