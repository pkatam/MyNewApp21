/* 
* Copyright (c) 2017 and Confidential to Pegasystems Inc. All rights reserved11.  
*/ 

pipeline {
    agent any

    options {
      timestamps()
      timeout(time: 15, unit: 'MINUTES')
      withCredentials([
        usernamePassword(credentialsId: 'PDM_JFrogRepository', 
            passwordVariable: 'P@ssw0rd_pega', 
            usernameVariable: 'pega_admin')
        /*usernamePassword(credentialsId: 'puneeth_export', 
            passwordVariable: 'rules', 
            usernameVariable: 'puneeth_export')*/
        ])
    }
    stages {
// in a declarative pipeline
        stage('Trigger Building') {
		                    steps {
						executeModuleScripts('build') // local method, see at the end of this script
				          }
				  }

           }	
}
// at the end of the file or in a shared library
void executeModuleScripts(String operation) {

            def allModules = ['module1', 'module2', 'module3', 'module4', 'module11']
            allModules.each { module ->  String action = "${operation}:${module}"  
           echo("---- ${action.toUpperCase()} ----") 
	   String command = "npm run ${action} -ddd"                   
           // here is the trick           
           script {

																								                stage(module) {
			if (module == 'module1') {
			                                                    echo 'I only execute on the master branch'
									                                                } else {
															                                                    echo 'I execute elsewhere'
																					                                                }
				}
                  }
	        }
				
}																		
