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
				sh "./mvn compile"
			}
		}

		stage('test-app'){
			steps{
				sh "./mvn test"
			}
		}

		stage('build-app'){
			steps{
				sh "./mvn package"
			}
		}

		stage('deploy'){
			steps{
				sh '''cd target
				      nohup java -jar -Dserver.port=8083 *.jar &&'''
			}
		}

	}
}