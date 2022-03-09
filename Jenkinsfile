pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('luizvnasc-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t luizvnasc/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push luizvnasc/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

