#!/usr/bin/env groovy

node ('master') {
	
	stage('Git checkout') {
		git branch: 'master', changelog: false, credentialsId: '1766cbec-c015-4682-91b1-5b66d41f5996', poll: false, url: 'git@github.com:tarunmittalid/exercise1.git'	
		}

    parallel (
        w1: {
            stage ("Start webapp 1"){
                // start web app 1
                echo "start web app 1"
            }
        },
        w2: {
            stage ("Start webapp 2"){
                // start web app 2
                echo "start web app 2"
            }
        }
        )

    parallel (
        getw1: {
            stage ("Access webapp 1"){
                // access web app 1
                echo "hello from web app 1"
            }
        },
        getw2: {
            stage ("Access webapp 2"){
                // access web app 2
                echo "hello from web app 2"
            }
        }
        )

	stage('User innput') {

        echo "Asking for user input"
        def userInput = input(
         id: 'userInput', message: 'Let\'s destroy?', parameters: [
         [$class: 'TextParameterDefinition', defaultValue: 'no', description: 'Destroy', name: 'input1']
        ])
        echo ("User Input: "+userInput['input1'])

        if ( userInput != "no" ){
            stage "Destroy all apps" {
    			// Stop web apps
                echo "stop web app 1"
                echo "stop web app 2"
            }
	        }

	}

}
