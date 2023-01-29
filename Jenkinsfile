pipeline{
	agent any
	stages{
		//opcional. Solo si queremos descargar la ultima imagen
		stage("Pull Latest Image"){
			steps{
				bat "docker pull vinsdocker/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				//para linux seria: sh "docker-compose up ..."
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up search-module book-flight-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			bat "docker-compose down"

		}
	}
		
	
}