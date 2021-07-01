pipeline {
	//agent any
	agent { node { label 'docker-slave-demo' } }
	
    	environment {
		DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    	}
    	stages {
        	stage('build') {
            		steps {
                		sh 'docker build -t docker.pkg.github.com/testuser681/microservice-sample-app/result:latest ./result'
				sh 'docker build -t docker.pkg.github.com/testuser681/microservice-sample-app/seed-data:latest ./seed-data'
				sh 'docker build -t docker.pkg.github.com/testuser681/microservice-sample-app/vote:latest ./vote'
				sh 'docker build -t docker.pkg.github.com/testuser681/microservice-sample-app/worker:latest ./worker'
            		}
        	}
		stage('login') { 
			steps {
		    		sh 'docker login https://docker.pkg.github.com -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'    
	    		}
		}
		stage('push') {
		    	steps { 
			    	sh 'docker push docker.pkg.github.com/testuser681/microservice-sample-app/result:latest'
			    	sh 'docker push docker.pkg.github.com/testuser681/microservice-sample-app/seed-data:latest'
			    	sh 'docker push docker.pkg.github.com/testuser681/microservice-sample-app/vote:latest'
			    	sh 'docker push docker.pkg.github.com/testuser681/microservice-sample-app/worker:latest'
		    	}
	    	}
    	}
	post {
	    always {  
                mail bcc: '', body: "<b>ERROR</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Build number -> ${env.BUILD_NUMBER}", to: "pdrabicki@griddynamics.com";  
            } 
	}
}

