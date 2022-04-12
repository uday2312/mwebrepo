

pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
 stage('CodeCheckout') {
            steps {
		git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
		echo "Stage-1 executed."
		  }
		   }

stage('CodeBuild') {
            steps {
		sh 'mvn clean install'
		echo "Stage-2 executed."
		  }
		  }

stage('CodeDeploy ') {
            steps {
		sshagent(['deploy_user']) {
			
		
sh "scp  -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@52.90.4.9:/opt/apache-tomcat-9.0.62/webapps"
					  }
		echo "Stage-3 executed."
		  }
		  }
	} 
}
