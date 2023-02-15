pipeline {
	agent any
	stages {
	    stage ('clean up') {
	        steps {
	            cleanWs()
	        }
	    }
	}
		stage ('build') {
			steps {
			    dir ('demo1'){
				    sh 'mvn clean install -DskipTests'
			    }
			}
		
		}
		stage ('test') {
			steps {
			    dir ('demo1'){
				    sh 'mvn test'
			    }
			}
			post {
				always {
				    dir ('demo1'){
					    junit 'target/surefire-reports/*.*xml'
				    }
				}
			}
		}
		stage ('run') {
			steps {
			    dir ('demo1'){
			    	sh './scripts/deliver.sh'
			    }
			}
		
		}
	}
}
