// SCRIPTED 
node {
	echo "Build"
	echo "Test"
	echo "Integration Test"
	
}
//Declerative pipeline
pipeline{
	agent any 
	//agent{docker { image 'maven:3.6.3'} }
	environment{
	mavenHome = tool 'myMaven'
	dockerHome = tool 'myDocker'
	PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
	}
	stages{
		stage('Build'){
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
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