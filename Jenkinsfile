// DECLARATIVE
pipeline{
	//agent {docker{image "node:16.0.0"}}
	agent any
	environment{
		dockerHome = tool "myDocker"
		mavenHome = tool "myMaven"
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				echo "Build"
				sh "docker --version"
				sh "mvn --version"
				echo "PATH - $env.PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
				echo "mvn failsafe:integration-test"
			}
		}
	}
	post{
		always{
			echo "I am awesome , I run always"
		}
		success{
			echo "I run when you are successful"
		}
		failure{
			echo "I run when you fail"
		}
	}
}

