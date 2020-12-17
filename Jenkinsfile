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
			def scannerHome = tool 'sonar_scanner';
    			
			withSonarQubeEnv('sonar') { 
      			sh "${scannerHome}/bin/sonar-scanner  -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build"
	//bat "${scannerHome}\\bin\\sonar-scanner -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build"

					}
 				
			}
			stage('Run'){
			sh 'nohup gradlew bootrun &'
			//bat "start gradlew bootRun"

			}

			 stage('Test'){
			sh 'sleep 20' 
			sh "curl -X GET 'http://localhost:8087/rest/mscovid/test?msg=testing'"

                        }

			stage('Nexus')
			{
			sh 'sleep 40'
			nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'test-nexus',
                	packages: [[ $class: 'MavenPackage', MavenAssetList: [[classifier: '', extensions: '' ,
                	filePath: './build/libs/DevOpsUsach2020-0.0.1.jar']],
                	mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', 
			packaging : 'jar', version: '0.0.1']]]
                        }
			}
		}
	}
}
}
