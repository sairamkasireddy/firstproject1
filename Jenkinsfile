pipline {
  
  agent any 
  
    stages{
    
      stage( "Github Credentials  to bulid with maven"){
        
         steps{
            git 'https://github.com/sairamkasireddy/firstproject1.git'
          }
      }
          
           
        stage( "Build  the file using maven"){
          steps{
            sh "mvn clean package"
            
          }
        }
       stage( "Deploy -Build into apache tomcat"){
          steps{
             sshagent(['Tomcat-pwd']) {
               
               sh """
                     scp -o StrictHostKeyChecking=no target/myweb.war   Linux@172.31.91.166:/root/apache-tomcat-9.0.69/webapps/                                        
                     ssh  Linux@172.31.91.166 /root/apache-tomcat-9.0.69/bin/shutdown.sh
                     ssh  Linux@172.31.91.166 /root/apache-tomcat-9.0.69/bin/startup.sh
                   """
   }
          }
  }
    }
}
        
      
    
          
          
