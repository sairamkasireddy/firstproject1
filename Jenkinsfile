pipline {
  agent any 
  
  Stages{
    stage( "Github Credentials  to bulid with maven")
          steps{
            git 'https://github.com/sairamkasireddy/firstproject1.git'
          }
          
           
    stage( "Build  the file using maven")
          steps{
            sh "mvn clean package"
            
          }
     stage( "Deploy -Build into apache tomcat")
          steps{
             sshagent(['Tomcat-pwd']) {
               
               sh """
   
      }
    
          
          
