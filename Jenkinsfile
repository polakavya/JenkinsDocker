pipeline {
    agent { label 'linux' }

    options {
        timeout(time: 30, unit: 'MINUTES')
        timestamps()
    }

    environment {
        CI = true
        DOCKER_REPOSITORY = 'pkavya/pythonapp'
        dockerImage = ''
	CREDENTIAL_ID='	docker_jenkins'    
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
