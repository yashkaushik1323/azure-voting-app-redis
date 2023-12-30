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
		stage('Check python version'){
			steps{
					bat(script: 'python --version')
				}
			}
		stage('Run Tests'){
			steps{
					bat(script: 'pytest ./tests/test_sample.py')
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
