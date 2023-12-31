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
					bat(script: 'docker compose build')
				}
			}
		stage('Start App'){
			steps{
					bat(script: 'docker compose up -d')
				}
			}
		stage('Run Tests'){
			steps{
					bat(script: 'python ./tests/test_sample.py')
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
				bat(script: 'docker compose down')
			}
		}
	}
