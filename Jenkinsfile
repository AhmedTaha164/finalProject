pipeline {
    agent any
    environment {     
    DOCKERHUB_CREDENTIALS= credentials('dockerhub')     
        
    } 

    stages {
        stage('Fetch code') {
            steps {
                git branch: 'main', credentialsId:"github" , url: 'https://github.com/AhmedTaha164/finalProject.git'
            }
        }
        
        
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'                		
	            echo 'Login Completed'     
            }
        }
        
        
        stage('building image') {
            steps {
                sh 'docker build -t  ahmedtaha164/finalproject:V1 .'
            }
       }
       
       
       stage('Push Image to Docker Hub') {         
            steps{                            
                sh 'docker push ahmedtaha164/finalproject:V1'           
                echo 'Push Image Completed'       
            }            
        }  
        
        
        
        
        stage('current dir') {
            steps {
                sh 'pwd'
                sh 'ls'
            }
        }
      
        stage('Test connection') {
            steps {
                sh 'chmod 600 /var/lib/jenkins/workspace/finalProject/ansible/m01/private_key'
                
                 sh 'chmod 600 /var/lib/jenkins/workspace/finalProject/ansible/m02/private_key'
                
                sh 'export ANSIBLE_HOST_KEY_CHECKING=False'

                sh "ansible all -m ping -i inventory "
                sh 'ansible-playbook -i inventory playbook.yml'

            }
        }

    }
}
