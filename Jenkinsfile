pipeline {
    agent any
       environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('checkout') {
            steps {
                git branch: 'main', credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/HelloServlet.git'
                echo 'Stage-1 done sucessfully.'
            }
          }
        stage('Build') {
            steps {
                    sh 'mvn clean package'
                    echo 'Code build done sucessfully.'
            }
          }
        stage('Stage-3') {
            steps {
               sshagent(['deploy_user']) {
   			
sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/PJOB-1/target/helloworld.war  ec2-user@18.117.224.145:/opt/apache-tomcat-9.0.93/webapps"
		}
            }
        }
 }
}
