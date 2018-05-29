podTemplate(label: 'jenkins-jnlp-auto') {
    node('jenkins-jnlp-auto') {
     	// Clean workspace before doing anything
        deleteDir()
    
        try {
            stage ('Clone') {
            	checkout scm
							branch 'master' of https://github.com/mtbvang/jenkinsfile-basic-sample
            }
            stage ('Build') {
            	sh "echo 'shell scripts to build project...'"
            }
            stage ('Tests') {
    	        parallel 'static': {
    	            sh "echo 'shell scripts to run static tests...'"
    	        },
    	        'unit': {
    	            sh "echo 'shell scripts to run unit tests...'"
    	        },
    	        'integration': {
    	            sh "echo 'shell scripts to run integration tests...'"
    	        }
            }
          	stage ('Deploy') {
                sh "echo 'shell scripts to deploy to server...'"
          	}
        } catch (err) {
            currentBuild.result = 'FAILED'
            throw err
        }
    }
}




