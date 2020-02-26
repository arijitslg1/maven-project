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
								sshagent (['172.31.93.122']) {
								sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.93.122:/var/lib/tomcat/webapps'
								}		
							}
					}
				}
			}
