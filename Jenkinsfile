pipeline {
  
  agent any 
  environment{
    PATH="/opt/apache-maven-3.8.6/bin:$PATH"
  }
  
    stages{
    
      stage( "Github_cred"){
        
         steps{
            git 'https://github.com/sairamkasireddy/firstproject1.git'
          }
      }
      stage( "maven_build"){
          steps{
            sh "mvn clean package"
            
          }
          }
      stage( "Tomcat_deploy"){
          steps{
            sshagent(['Tomcat-pwd']) {
   

              
                   sh "scp -o StrictHostKeyChecking=no  target/demo.war   ec2-user@13.233.140.44:/opt/tomcat/webapps/" 
                  sh  "ssh ec2-user@13.233.140.44 /opt/tomcat/bin/sh shutdown.sh"
                   sh  "ssh ec2-user@13.233.140.44 /opt/tomcat/bin/sh startup.sh"
                   
              
            }
          }
      }
    }
}
     
         
        
        
   
