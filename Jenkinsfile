pipeline {
	agent any

	stages{	
		stage('checkout') {
			steps{ 	
				echo "Checking out the  code....."
				checkout([$class: 'GitSCM', branches: [[name: '*/main']],
    userRemoteConfigs: [[url: 'https://github.com/Tanujsingh25/gs-spring-boot.git']]])
				
			}
		}
		
		stage('clean-app'){
			steps{
				sh "mvn clean"
			}
		}
		
		stage('compile-app'){
			steps{
				sh "mvn compile"
			}
		}

		stage('test-app'){
			steps{
				sh "mvn test"
			}
		}

		stage('build-app'){
			steps{
				sh "mvn packageclean"
			}
		}

	}
}