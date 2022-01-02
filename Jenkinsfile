pipeline {
	agent any
	tools { 
      maven 'MVN_HOME' 
    }
	//agent {docker { image 'node:13.8'}}
	environment {
		mavenHome = 'myMaven1047'
		dockerHome = 'MyDocker1047'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	
	stages{
		stage('Build'){
			steps{
				sh "mvn --version"
                sh "docker version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile'){
			steps{
			  
                   sh "mvn clean compile"
              
				
			}
		}
		stage('Test'){
			steps{
             echo "Test"
			sh "mvn test"
			}
			
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
				sh "mvn failsafe:integration-test failsafe:verify"
				
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
