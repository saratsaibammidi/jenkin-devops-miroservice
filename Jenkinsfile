//Declarative
pipeline{
	agent any
	  //agent{docker {image 'maven:3.9.9'}}
		enviroment{
			dockerHome = tool 'myDocker'
			mavneHome = tool 'myMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages{
			stage('Build') {
				steps{
					sh 'mvn --version'
					sh 'docker version'
					echo "Build"
					echo "PATH -$PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
					echo "JOB_NAME - $env.jOB_NAME"
					echo	"BUILD_TAG - $env.BUILD_TAG"
					echo "BUILD_URL -$env.BUILD_URL"

				}
			}
			stage('test') {
				steps{
					echo "Test"
				}
			}
			stage('Integration test'){
				steps{
					echo "Integration Test "
				}
			}
		}
}