pipeline {
	agent { docker { image 'python:latest' }}
    stages {
			stage('1-Design') {
				steps {
					echo 'Start creating the World'
					echo 'Creating the World...'
					echo 'The World created successfully'
            }
			}
            stage('Coding') {
				steps {
					echo 'Coding the World'
            }
			}
            stage('Testing') {
				steps {
					echo 'Testing the World'
            }
			}
            stage('Release') {
				steps {
					echo 'Releasing the World'
            }
			}
            stage('Support') {
				steps {
					echo 'Supporting the World'
					sh "python --version"
            }
        }
    }
}
