pipeline {
    agent any

    stages {
        stage('SCM Checkout') 
	   
	    {
            steps {
		  git "https://github.com/m1m2m3/Repo2.git"
	          }
            }
        
           stage('build && SonarQube analysis') 
	    {
            steps {
                withSonarQubeEnv(credentialsId: 'abc', installationName: 'Sonar') 
		    {
                 withMaven(jdk: 'myjdk', maven: 'mymaven') 
			    {
                        sh 'mvn clean package sonar:sonar'
                            }
                   }
                }
           }
	    
	   stage ('Deploy to Tomcat') 
	    {
	   steps{
           sshagent(['54.175.245.41']) 
		   {
                   sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@54.175.245.41:/var/lib/tomcat/webapps'
                    }
                }
           }

 }
}
