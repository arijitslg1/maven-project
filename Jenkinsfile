pipeline {
    agent any


    stages 
    {  
        
        stage ('SCM Checkout') {
          git 'https://github.com/arijitslg1/maven-project'
         }
    
    }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') 
                {   
                    sh 'mvn compile' 
                }
                }
                  }
                                
            
        
        
        stage ('Testing Stage') {


            steps {
                withMaven(maven : 'LocalMaven')
                {
                    sh 'mvn test'
                }
                  }
                                 
        }

        
        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven')
                {
                    sh 'mvn install'
                }
                                  
                   }
        }
        
        stage ('deploy to tomcat') {
            steps {
                sshagent(['12af884e-6a7c-4a6c-b452-ddeb89398b45']) {
                sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.56.216:/var/lib/tomcat/webapps'
                } 

    }      
}
