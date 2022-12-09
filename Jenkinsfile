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
            sshagent(['Tomcat']) {
              sh """
                     scp -o StrictHostKeyChecking=no  target/*.war    ec2-user@65.0.132.133:/opt/apache-tomcat-10.0.27/webapps/                                        
                     ssh  ec2-user@65.0.132.133 /opt/apache-tomcat-10.0.27/bin/shutdown.sh
                     ssh  ec2-user@65.0.132.133 /opt/apache-tomcat-10.0.27/bin/startup.sh
                """
   
}
            
          
          }
        
            
          }
          }
        
        
    }

          
           
       
