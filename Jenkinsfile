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
           stage("Sonar_quality") {
           steps{
            withSonarQubeEnv('sonarqube'){ 
            sh "${mavenCMD} sonar:sonar"  
          
          }
          }
           stage( "Tomcat_deploy"){
          steps{
            sshagent(['tomcat']) {
   

              
                   sh "scp -o StrictHostKeyChecking=no  target/demo.war   ec2-user@172.31.43.171:/opt/tomcat/webapps/" 
                  
                   
              
            }
          }
      }
      
    }
}
                             }
     
         
        
        
   
