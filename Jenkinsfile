pipeline {
    agent any	
	 
 stages {
      stage('checkout') {
           steps {             
                git branch: 'master', url: 'https://github.com/meghashirani/hello-world-war.git'             
          }
        }       

  stage('Docker Build and Tag') {
           steps {  
		 
                sh 'sudo docker build -t my_new_tomcat:latest .' 
                sh 'sudo docker tag my_new_tomcat meghashirani/my_new_tomcat:latest' 
            }
        }

stage('Login to Docker hub') {
           steps {
              
                sh 'sudo docker login --username=meghashirani --password=Mandidoc@561995'
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
       	  sh  'sudo docker push meghashirani/my_new_tomcat:latest'  
        }                 
          
        }     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
	      {
                sh "sudo docker run -d -p 8004:8080 meghashirani/my_new_tomcat:latest"
             }
        }
 
    }
	}
