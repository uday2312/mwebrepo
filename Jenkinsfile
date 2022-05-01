pipeline {
    agent any
environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
               stage('CodeCheckout') {
            steps {
               git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
                echo 'Codecheckout Executed.'
                   }
			}
        stage('CodeBuild') {
            steps {
               
               sh 'mvn clean install'
                echo 'CodeBuild executed.'
                   }
			}
stage('CodeDeploy') {
            steps {
               sshagent(['deploy_user']) {
   		sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@3.221.163.207:/opt/apache-tomcat-9.0.62/webapps'   
				}
                echo 'CodeDeploy executed.'
                   }
			}
            }
      }
