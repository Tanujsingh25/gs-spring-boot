pipeline {
	agent any

	stages{	
		stage('checkout') {
			steps{ 	
				echo "Checking out the  code....."
				checkout([$class: 'GitSCM', branches: [[name: '*/$branch']],
    userRemoteConfigs: [[url: 'https://github.com/Tanujsingh25/gs-spring-boot.git']]])
				
			}
		}

		stage ('clean') {
			steps{
				sh '''cd complete
				./mvnm clean'''
			}
		}

		stage ('Run - code') {
			steps{
				cd complete
				./mvnm compile
			}
		}

		stage (test- code) {
			steps{
				cd complete
				./mvnm test
			}
		}

		stage (build-app) {
			steps{
				cd complete
				./mvnm package
			}
		}


		
	}
}