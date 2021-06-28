pipeline {
	agent {
		docker {
        		image 'maven:3.8.1-adoptopenjdk-11'
        		label 'docker-slave-demo'
        		args  '-v /var/run/docker.sock:/var/run/docker.sock'
    }
	}
    environment {
	DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
        stage('build') {
            steps {
                sh 'docker build -t docker.pkg.github.com/testuser681/microservice-sample-app/result:latest ./result'
            }
        }
    }
}
