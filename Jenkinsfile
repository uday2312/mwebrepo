pipeline {
    agent any
	environment {
        PATH = "/opt/maven/bin:$PATH"
    }
     stages {
        stage('CodeCheckout') {
            steps {
		git credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
		echo "CodeCheckout is executed."
		  }
				}
	
        stage('CodeBuild') {
            steps {
		sh 'mvn clean install'
		echo "CodeBuild is executed."
		  }
				}
	
        stage('CodeDeploy') {
            steps {
		sshagent(['deploy_user']) {
	sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@3.94.150.143:/opt/apache-tomcat-9.0.63/webapps"
    echo "CodeDeploy is executed."
}
		  }
				}
	
        stage('Stage-4') {
            steps {
		echo "Stage-4 is executed."
		  }
				}
	}
}
