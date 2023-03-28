// SCRIPTED 
node {
	echo "Build"
	echo "Test"
	echo "Integration Test"
	
}
//Declerative pipeline
pipeline{
	agent any 
	stages{
		stage('Build'){
			steps {
				echo "This is build stage"
				}
			}
		stage('Test'){
			steps{
				echo "This is test stage"
				}
			}
		stage('Integration Test'){
			steps{
				echo "This is integration testing stage"
				}
			}
    }
}