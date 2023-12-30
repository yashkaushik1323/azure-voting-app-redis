pipeline {
	agent any
	
	stages {
		stage('Verify Branch'){
			steps{
					echo "$GIT_BRANCH"
				}
			}
		stage('Docker Build'){
			steps{
					bash(script: 'docker compose build')
				}
			}
		stage('Start App'){
			steps{
					bash(script: 'docker compose up -d')
				}
			}
		stage('Run Tests'){
			steps{
					bash(script: 'pytest ./tests/test_sample.py')
				}
			post {
				success {
					echo "Test Passed"
				}
				failure {
					echo "Test Failed"
				}
			}
			}
		}
		post {
			always {
				bash(script: 'docker compose down')
			}
		}
	}
