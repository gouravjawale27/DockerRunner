pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				bat "docker pull gouravjawale/selenium-dockerwithjenkins"
			}
		}
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up livings-liquid"
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