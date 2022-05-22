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
				sh '''cd complete
					  ls -lrth; ./mvnw clean'''
			}
		}
		
		stage('compile-app'){
			steps{
				sh '''cd complete
					  pwd
					  ./mvnw compile'''
			}
		}

		stage('test-app'){
			steps{
				sh '''cd complete
					  pwd
					  ./mvnw test'''
			}
		}

		stage('build-app'){
			steps{
				sh '''cd complete
					  pwd
					  ./mvnw package'''
			}
		}

		stage('deploy'){
			steps{
				sh "BUILD_ID=dontKillMe nohup java -jar -Dserver.port=8083 complete/target/*.jar &"
			}
		}
	}
}