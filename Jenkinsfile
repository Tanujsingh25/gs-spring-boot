pipeline {
	agent any

	stages{	
		stage('checkout') {
			steps{ 	
				echo "Checking out the  code....."
							
			}
		}

		stage ('clean') {
			steps{
				sh '''cd complete
				./mvnwclean'''
			}
		}

		stage ('Run - code') {
			steps{
				sh '''cd complete
				./mvnw compile'''
			}
		}

		stage ('test- code') {
			steps{
				sh '''cd complete
				./mvnw test'''
			}
		}

		stage ('build-app') {
			steps{
				sh '''cd complete
				./mvnw package'''
			}
		}


		
	}
}