pipeline {
	agent any
	stages{
		stage('Build'){
			steps{
				echo "Build"
			}
		}
		stage('Test'){
			steps{
             echo "Test"
			}
			
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
			}
		}
	}
	post {
		always {
			echo "I am always successfull"
		}
		success {
			echo "Successfull"
		}
		failure {
			echo "failure"
		}

	}
	
}
