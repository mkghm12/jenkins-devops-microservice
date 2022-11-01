pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
				// sh 'mvn --version'
				echo 'Build'
				echo '$PATH'
				echo 'BUILD_NUMBER - $BUILD_NUMBER'
				echo '$env.BUILD_ID'
				echo '$env.JOB_NAME'
				echo '$env.BUILD_TAG'
				echo '$env.BUILD_URL'
			}
		}
		stage('Test'){
			steps{
				echo 'Test'
			}
		}
		stage('IntegrationTest'){
			steps{
				echo 'Integration Test'
			}
		}
	}
}