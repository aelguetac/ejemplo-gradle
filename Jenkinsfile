pipeline {
    agent any

	parameters { choice (name: 'herramienta', choices : ['gradle','maven'], description :'')}

	stages {
        	stage('Pipeline') {
            		steps {
                		script {
					env.TAREA = ''
					//def cadena = "hola ${params.buildtool}"
					def cadena = "{env.TAREA}"
					printl("buildtool usada $(params.herramienta)")
					if (params.herramienta == 'gradle' ){
					        def ejecucion = load 'gradle.groovy'
					        ejecucion.call()
	
					} else {
					        def ejecucion = load 'gradle.groovy'
                                                ejecucion.call()

					}
			
                        }
			}
		}
	}
		post {

			success {
				//println env.TAREA
				//println env.JOB_NAME
				//println params.buildtool

				//def subject = "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
				def mensajes = "Build status ${buildStatus}: [Alejandro Elgueta] [${params.herramienta}] Ejecución exitosa"
//	Build Success: [Nombre Alumno][Nombre Job][buildTool] Ejecución exitosa.
//	Build Failure: [Nombre Alumno][Nombre Job][buildTool] Ejecución fallida en stage [Stage]

				slackSend color: 'good', message: '"${mensajes}"', teamDomain: 'devops-usach-2020', tokenCredentialId: 'slack'
			}
			failure {
				def mensajef = "Build status ${buildStatus}: [Alejandro Elgueta] [${params.herramienta}] Ejecución fallida en stage [${TAREA}]"
                                //println env.TAREA." "env.JOB_NAME
				slackSend color: 'danger', message: '"${mensajef}"', teamDomain: 'devops-usach-2020', tokenCredentialId: 'slack'				

			}
		}

	
}

