pipeline {
    agent any
    
    tools{
        maven 'maven3.9.6'
    }
    stages {
        stage('Git-Checkout') {
            steps {
                git 'https://github.com/ABCello/mvnwebapp.git'
            }
        }
        
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
        
        stage('Deploy To Container'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'TomcatCredential', path: '', url: 'http://52.90.225.114:8080/manager/html')], contextPath: 'mvnwebapp', war: '**/mvnwebapp.war'
            }
        }
    }//stages closing
    
}//pipeline closing
