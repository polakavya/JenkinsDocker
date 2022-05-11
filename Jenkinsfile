pipeline {
    agent any
	environment{
	   dockerImage = ''
	   registry = 'pkavya/pythonapp'	
	
	}
	

stages{	
      stage('build') {
            steps {
		    script{
		           dockerImage = docker.build registry
		          }
                echo 'build'      
	        }
                    }
      stage('Push') {
            steps {
              
                echo 'Prod'
                   
	    }
        }
                   
}
}
