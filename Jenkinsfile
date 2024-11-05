pipeline {
	agent any

	stages {
		stage('Checkout'){
			steps {
				git branch: 'main', url: 'https://github.com/patty2904/lbg-vat-calculator.git'
			}
		}
		stage('SonarQube Analysis'){
			environment {
				scannerHome = tool 'sonarqube'
			}
				steps {
					withSonarQubeEnv('sonarqube-pc') {
						sh "${scannerHome}/bin/sonar-scanner"
					}
				timeout(time:10, unit: 'MINUTES'){
                    			waitForQualityGate abortPipeline: true
                }
				}
		}
	}
}
