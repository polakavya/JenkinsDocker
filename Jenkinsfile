pipeline {
    
    

    environment {
        CI = true
        DOCKER_REPOSITORY = 'docker.com/docker_jenkins'
        RegistryCredential = 'dockerhub'
        dockerImage = ''
      }
agent any
    stages {
        stage('Build Image') {
            steps {
                script {
			dockerImage = docker.build("${DOCKER_REPOSITORY}/kavya:${BUILD_NUMBER}")
			
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry(" ", "${registryCredential}") {
                        dockerImage.push()
		  
                    }
                }
            }
        }

	   
    }
}
