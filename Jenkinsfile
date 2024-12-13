pipeline {
    agent any
   environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    
    stages {
        stage('Checkout') {
            steps {
    git branch: 'main', credentialsId: 'git_credentials', url: 'https://github.com/t-shashikanth/HelloServlet.git'
                echo 'Code Checkout done sucessfully.'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean install"
                echo 'Code build done sucessfully.'
            }
        }
        
        stage('deploy') {
            steps {
                
        sshagent(['deploy_user']) {
       sh "scp -o StrictHostKeyChecking=no  /var/lib/jenkins/workspace/JOB-1/target/helloworld.war  ec2-user@18.219.13.193:/opt/apache-tomcat-9.0.98/webapps/ "
       }
                
                
                echo 'Code deploy done sucessfully.'
            }
        }
    }
}
