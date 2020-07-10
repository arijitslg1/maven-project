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
             withMaven(jdk: 'localjdk-1.8', maven: 'localmaven') {
             sh 'mvn compile'
	   }
         }
       }
      
       stage('please test code')
       { 
	   steps {
             withMaven(jdk: 'localjdk-1.8', maven: 'localmaven') {
              sh 'mvn test'
	    }
         }
       }

       stage('please build code')
       { 
	   steps {
             withMaven(jdk: 'localjdk-1.8', maven: 'localmaven') {
             sh 'mvn package'
	    }
         }
       }
   }
}
	   
