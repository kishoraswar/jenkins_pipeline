pipeline {  
   agent any
   environment{
       PATH="/maven/apache-maven-3.8.6/bin:$PATH"
   }
 
    stages {  
            stage ('Git-Checkout') {  
                steps{
                    git 'https://github.com/kishoraswar/Pipeline-project-deployment-on-Tomcat.git'
                    echo "Checkout successful";
                  
                    
                } 
            }
            stage ('Compile') {  
                  steps{
                    sh  "mvn compile"
                    echo "compile successful";
                    
                } 
            }
            stage ('Build') {  
                  steps{
                    sh "mvn clean"
                    sh "mvn package"
                    echo "build successful";
                    
                } 
            }
             stage ('Test') {  
                  steps{
                    sh "mvn test"
                    echo "test successful";
                } 
            }
            
        stage ('Dev-Deploy') {
            steps{
            deploy adapters: [tomcat9(credentialsId: 'tomcat_deployer', path: '', url: 'http://18.222.226.52:8080/')], contextPath: 'myapp', onFailure: false, war: '**/*.war'
             echo "Deploy successful";
                
            }
        }
         stage ('Uat-Deploy') {
            steps{
            deploy adapters: [tomcat9(credentialsId: 'tomcat_deployer', path: '', url: 'http://18.222.226.52:8080/')], contextPath: 'myapp', onFailure: false, war: '**/*.war'
             echo "Deploy successful";
                
            }
        }
         stage ('prod-Deploy') {
            steps{
            deploy adapters: [tomcat9(credentialsId: 'tomcat_deployer', path: '', url: 'http://18.222.226.52:8080/')], contextPath: 'myapp', onFailure: false, war: '**/*.war'
             echo "Deploy successful";
                
            }
        }
        
        }
    }
