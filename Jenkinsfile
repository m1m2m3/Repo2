pipeline 
{
    agent any

    stages 
{
        stage('SCM Checkout') 
	    {
            steps {
		  git "https://github.com/m1m2m3/Repo2.git"
	          }
            }
        stage('Test') 
	    {
            steps 
		{
           withMaven(jdk: 'myjdk', maven: 'mymaven')
					{
					sh 'mvn test'      
					}    
		}
           }
       
}
}
