pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Docker Credentials')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t ubuntu:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push ubuntu:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}