pipeline {
    agent any

    stages {
        stage('Pipeline') {
            steps {
                script {
			stage('build test') {
			

            
	    		}
			stage('sonar') {
			stage('SonarQube analysis') {
			def scannerHome = tool 'sonar';
    			
			withSonarQubeEnv('sonar') { 
      				sh "${scannerHome}/bin/sonar-scanner"
			 	   }
 				}
			}
			stage('Run'){


			}

			 stage('Test'){


                        }

			stage('Nexus'){


                        }
			}
		}
	}
}
}
