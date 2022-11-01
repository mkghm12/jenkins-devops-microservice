pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
				// sh 'mvn --version'
				echo 'Build'
				echo "$PATH"
				echo "BUILD_NUMBER - $BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URl - $env.BUILD_URL'
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