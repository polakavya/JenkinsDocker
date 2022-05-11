pipeline {
    agent { label 'linux' }

    options {
        timeout(time: 30, unit: 'MINUTES')
        timestamps()
    }

    environment {
        CI = true
        DOCKER_REPOSITORY = 'hub.docker.com/pkavya/pythonapp'
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
                    docker.withRegistry("${DOCKER_REPOSITORY}", "${CREDENTIAL_ID}") {
                        dockerImage.push()
		  
                    }
                }
            }
        }
	    
	
	   
    }
