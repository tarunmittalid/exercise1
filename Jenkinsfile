#!/usr/bin/env groovy

node ('master') {
	
	stage('Git checkout') {
		git branch: 'master', changelog: false, credentialsId: '1766cbec-c015-4682-91b1-5b66d41f5996', poll: false, url: 'git@github.com:tarunmittalid/exercise1.git'	
		}

    parallel (
        w1: {
            stage ("Start webapp 1"){
            // start web app 1
            }
        },
        w2: {
            stage ("Start webapp 2"){
            // start web app 2
            }
        }
        )

    parallel (
        getw1: {
            stage ("Access webapp 1"){
            // access web app 1
            }
        },
        getw2: {
            stage ("Access webapp 2"){
            // access web app 2
            }
        }
        )

	stage('User innput') {

        echo "Asking for user input"
        try{
                timeout(time: 60, unit: 'SECONDS') {
                    doDestroy = input(
                        id: 'Proceed1', message: 'Continue destroying?', parameters: [
                        [$class: 'BooleanParameterDefinition', defaultValue: 'no', description: '', name:'Continue the destroy']
                    ])
                }
            }
            catch(err) {
                doDestroy='no'
                echo "Timeout occured, destroy is not continuing"
            }

        if (doDestroy){
            stage "Destroy all apps"
			// Stop web app
	        }

	}

}