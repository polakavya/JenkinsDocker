pipeline {
    agent any
    environment {
        registry = 'pkavya/docker_jenkins'
        registryCredential = 'pkavya'
        dockerImage = ''
      }
stages{	
      stage('build') {
            steps {
                script{
			dockerImage = docker.build("pkavya/docker_jenkins")
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
}
