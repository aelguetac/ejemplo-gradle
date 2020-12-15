pipeline {
    agent any

    stages {
        stage('Pipeline') {
            steps {
                script {
			stage('build test') {
			sh "./gradlew clean build"
			
            
	    		}
			stage('sonar') {
			stage('SonarQube analysis') {
			def scannerHome = tool 'sonar_scanner';
    			
			withSonarQubeEnv('sonar') { 
      				sh "${scannerHome}/bin/sonar-scanner  -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build"
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
