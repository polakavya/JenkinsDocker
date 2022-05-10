pipeline {
    agent any
    environment {
        CI = true
        registry = 'docker.com/docker_jenkins'
        registryCredential = 'dockerhub'
        dockerImage = ''
      }

    stages {
        stage('Dev from Github') {
            steps {
                echo 'Hello World'
            }
        }
      stage('build from Github') {
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
                docker.withRegistry(" ", "dockerhub") {
                        dockerImage.push()
		  }
                echo 'Prod'
            }
        }
    }
}
}
