pipeline {
    agent { label 'any' }

    options {
        timeout(time: 30, unit: 'MINUTES')
        timestamps()
    }

    environment {
        CI = true
        DOCKER_REPOSITORY = 'docker.com/docker_jenkins'
        RegistryCredential = 'dockerhub'
        dockerImage = ''
      }

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
                    docker.withRegistry("${dockerImage}", "${registryCredential}") {
                        dockerImage.push()
		  
                    }
                }
            }
        }

	   
    }
}
