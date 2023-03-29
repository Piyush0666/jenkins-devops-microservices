// BUILD_TAG_FOR_THIS_BUILD:-jenkins-jenkins-devops-microservices-pipeline-13
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
		stage('Checkout'){
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				// echo "This is build stage"
				}
			}
		stage('Complie'){
				steps{
					sh "mvn clean compile"
				}
			}

		stage('Test'){
			steps{
				sh "mvn test"
				// echo "This is test stage"
				}
			}
		stage('Integration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
				// echo "This is integration testing stage"
				}
			}
			stage('Package'){ //"This will create jar file and this file we will use used and 
				steps{		//then it will build the image bcz we need to first build the jar
					sh "mvn package -DskipTests" //file and the we need to used it for building the docker image".
				}
			}
		stage('Build Docker Image'){
			steps{
		//		"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG" so this is a kind of primitive way
				script{
					dockerImage = docker.build("developmentoperation/currency-exchange-devops:${env.BUILD_TAG}")
			}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('' ,'dockerhub'){
					dockerImage.push();
					dockerImage.push('latest')
					}
				}
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