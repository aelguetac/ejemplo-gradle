pipeline {
    agent any

	parameters { choice (name: 'herramienta', choices : ['gradle','maven'], description :'')}

	stages {
        	stage('Pipeline') {
            		steps {
                		script {
					//env.TAREA = ''
					//def cadena = "hola ${params.buildtool}"
					def cadena = "{env.TAREA}"
					echo params.herramienta
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
		post{

			sucess {
				println env.TAREA
				println env.JOB_NAME
				println params.buildtool
				def mensaje = "{env.TAREA} "
				slackSend color: 'good', message: '[Alejandro Elgueta][JOB_NAME]', teamDomain: 'devops-usach-2020', tokenCredentialId: 'slack'
			}
			failure {
                                println env.TAREA." "env.JOB_NAME
				slackSend color: 'danger', message: '[Alejandro Elgueta][JOB_NAME]', teamDomain: 'devops-usach-2020', tokenCredentialId: 'slack'				

			}
		}

	}
}

