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
	post {
		always{
			echo 'This is awsome. I run always'
		}
		success{
			echo 'This will run when stages are successfully build'		
		}
		failure{
			echo 'This will run when build get failed'
		}
	}
}