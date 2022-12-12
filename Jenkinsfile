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
     
        stage('nexus artifact') {
           steps{
             nexusArtifactUploader artifacts: [[artifactId: 'demo', classifier: '', file: 'target/demo.war', type: 'war']], credentialsId: 'nexus-pwd', groupId: 'com.domain', nexusUrl: '52.66.205.225:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'html-project', version: '1.0-SNAPSHOT'
             
           
}
}
      
      stage( "Tomcat_deploy"){
          steps{
           sshagent(['tomcat_pwd']) {
   

              
                   sh "scp -o StrictHostKeyChecking=no  target/demo.war   ec2-user@3.110.160.172:/opt/tomcat/webapps/" 
                  
                   
              
            }
          }
      }
         
    }
    }


                             
     
        
        
        
   
