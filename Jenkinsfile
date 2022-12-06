pipeline {
  
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
    }
}
          
           
       
