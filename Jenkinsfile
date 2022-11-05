pipeline{
	agent any
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo 'Build'
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URl - $env.BUILD_URL"
			}
		}
		stage('Compile'){
			steps{
				sh 'mvn clean compile'
			}
		}
		stage('Test'){
			steps{
				sh 'mvn test'
			}
		}
		stage('IntegrationTest'){
			steps{
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
		stage('Package'){
			steps{
				sh 'mvn package -DskipTests'
			}
		}
		stage('Build Docker Image'){
			steps{
				script{
					dockerImage = docker.build("mkghm12/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('','dockerHub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}
	}
}