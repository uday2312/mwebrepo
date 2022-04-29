
pipeline {

  agent any
  environment {
        PATH = "/opt/maven/bin:$PATH"
    }

 stages{

      stage("CodeCheckout")
	    {
	      steps
		{
		  git branch: 'master', credentialsId: 'git_credentials', url: 'https://github.com/shashikanth-t/mwebrepo.git'
		  echo "CodeCheckout  executed."
		}
	         
	    }
      stage("CodeBuild")
	    {
	      steps
		{
		  sh "mvn clean package"
		  echo "Code build done sucessfully."
		}
	         
	    }
      stage("CodeDeploy")
	    {
	      steps
		{
		sshagent(['deploy_user']) {
    			
		sh "scp -o StrictHostKeyChecking=no  webapp/target/webapp.war  ec2-user@100.27.41.57:/opt/apache-tomcat-9.0.62/webapps"

					 }
		  echo "CodeDeploy executed."
		}
	         
	    }

       }

}
