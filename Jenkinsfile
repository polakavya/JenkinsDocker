pipeline {
    agent any
    environment {
        registry = 'pkavya/pythonapp'
        registryCredential = 'docker_jenkins'
        dockerImage = ''
      }
      stage('build from Github') {
            steps {
                script{
			dockerImage = docker.build("pkavya/pythonapp")
                }

                echo 'build'      
	    }
        }
      stage('Push') {
            steps {
                
                script{
                docker.withRegistry(" ", "docker_jenkins") {
                        dockerImage.push()
		  }
                echo 'Prod'
            }
        }
    }
}

		    
