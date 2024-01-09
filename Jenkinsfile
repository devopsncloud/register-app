pipeline {
	agent{ label 'Jenkins-Agent' }
	tools {
		jdk 'java17'
		maven 'maven3'
	}

	stages{
		stage("Cleanup Workspace"){
			steps{
			cleanWs()
			}
	}

		stage ("Checkout from SCM"){
	           steps{
			   checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/devopsncloud/register-app.git']])
		   }   
              }


		stage ("Build Application"){
			steps{
				
			}
		}
		


		
}
}

	











	
