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
			dockerImage = docker.build("${registry}")
                      }

                echo 'build'      
	        }
                    }
      stage('Push') {
            steps {
                
                script{
                docker.withRegistry(" ", "pkavya") {
                        dockerImage.push()
		                                           }
                echo 'Prod'
                    }
                }
                   }
}
}
