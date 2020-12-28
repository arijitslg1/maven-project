pipeline
{
   agent any
	
 //  tools {
 // Install the Maven version configured as "M3" and add it to the path.
 //    maven 'LocalMaven'
 //    jdk 'LocalJDK'
 //  }
	
   stages
   { 
       stage('scm checkout')
       {
           steps {
               git branch: 'master', url: 'https://github.com/arijitslg1/maven-project'
         }
       }

       stage('please compile code')
       { 
	   steps {
             withMaven(jdk: 'LocalJDK', maven: 'localmaven') {
             sh 'mvn compile'
	   }
         }
       }
      
       stage('please test code')
       { 
	   steps {
             withMaven(jdk: 'LocalJDK', maven: 'localmaven') {
              sh 'mvn test'
	    }
         }
       }

       stage('please build code')
       { 
	   steps {
             withMaven(jdk: 'LocalJDK', maven: 'localmaven') {
             sh 'mvn package'
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
