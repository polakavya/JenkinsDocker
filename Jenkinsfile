pipeline {
    agent any
    environment {
        registry = 'pkavya/pythonapp'
        registryCredential = 'docker_jenkins'
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
}
