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
			   checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/devopsncloud/register-app.git']])
		   }   
              }


		stage ("Build Application"){
			steps{
				sh "mvn clean package"
				
			}
		}
		stage ("Test Application"){
			steps{
				sh "mvn test"
			}
		}
		       stage("SonarQube Analysis"){
           steps {
	           script {
		        withSonarQubeEnv(credentialsId: 'jenkins-sonar-token') { 
                        sh "mvn sonar:sonar"
		        }
	           }	
           }
       }

}
}

