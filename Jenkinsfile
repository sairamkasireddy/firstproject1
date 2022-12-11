pipeline {
  
  agent any 
  environment{
    PATH="/opt/apache-maven-3.8.6/bin:$PATH"
  }
  
    stages{
    
      stage( 'Github_cred'){
        
         steps{
            git 'https://github.com/sairamkasireddy/firstproject1.git'
          }
      }
      stage( 'maven_build'){
          steps{
            sh "mvn clean package"
            
          }
          }
         stage('nexus artifact') {
           steps{
             nexusArtifactUploader artifacts: [[artifactId: 'demo', classifier: '', file: 'target/demo.war', type: 'war']], credentialsId: 'nexus-pwd', groupId: 'com.domain', nexusUrl: 'http://15.206.75.93:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'html-project', version: '1.0-SNAPSHOT'
             
           
}
}
    }
}

                             
     
         
        
        
   
