//Declarative
pipeline{
	  agent{docker {image 'maven:3.6.6'}}
		stages{
			stage('Build'){
				steps{
					sh 'mvn --version'
					echo "Build"
				}
			}
			stage('test'){
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