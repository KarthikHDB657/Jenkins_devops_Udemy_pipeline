pipeline {
	agent any
	//agent {docker { image 'node:13.8'}}
	environment {
		dockerHome = tool 'MyDocker1047'
		mavenHome = tool 'myMaven1047'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		registry = "kbhd1047/currency-exchange-devops"
        registryCredential = 'dockerhub'

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
		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage("Build docker image"){
			steps{
				script{
					dockerImage = docker.build("kbhd1047/currency-exchange-devops:${env.BUILD_TAG}")
				}
				
			}
		}
		stage("Push Docker image"){
			steps{
			 script{
				    docker.withRegistry('',registryCredential) {
				    dockerImage.push();
				 }

			    }
				
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
