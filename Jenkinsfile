pipeline {
	agent {
		docker { image 'node:14-alpine' }
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
