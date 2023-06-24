pipeline {
    agent any
	    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('CodeCheckout') {
            steps {
               git credentialsId: 'git_credentials', url: 'https://github.com/uday2312/mwebrepo.git'
               echo 'CodeCheckout executed.'
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
			sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ubuntu@3.21.206.193:/opt/apache-tomcat-9.0.64/webapps"
			echo ""
								}			
            }
			}
        }
    }
	
	
