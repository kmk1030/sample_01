pipeline {
	agent any

//	triggers {
//		pollSCM 'H/10 * * * *'
//	}

//	options {
//		disableConcurrentBuilds()
//		buildDiscarder(logRotator(numToKeepStr: '14'))
//	}

	stages {
		stage('github clone') {
            steps() {
				git branch: 'main', credentialsId: 'kmk1030',
				url: 'https://github.com/kmk1030/sample_01'
            }
        }
		stage('Build') {
			steps {
				sh '''
					echo 'Build ....'
					pwd
					ls -al
					./gradlew build
				'''
			}
		}
		stage('Check jar') {
			steps {
				sh '''
					echo 'Check jar...'
					ls -al ./build/libs
				'''
			}
		}
	}
}
/*
	stages {
		stage("test: baseline (jdk8)") {
			agent {
				docker {
					image 'adoptopenjdk/openjdk8:latest'
					args '-v $HOME/.m2:/tmp/jenkins-home/.m2'
				}
			}
			options { timeout(time: 30, unit: 'MINUTES') }
			steps {
				sh 'test/run.sh'
			}
		}

	}

	post {
		changed {
			script {
				slackSend(
						color: (currentBuild.currentResult == 'SUCCESS') ? 'good' : 'danger',
						channel: '#sagan-content',
						message: "${currentBuild.fullDisplayName} - `${currentBuild.currentResult}`\n${env.BUILD_URL}")
				emailext(
						subject: "[${currentBuild.fullDisplayName}] ${currentBuild.currentResult}",
						mimeType: 'text/html',
						recipientProviders: [[$class: 'CulpritsRecipientProvider'], [$class: 'RequesterRecipientProvider']],
						body: "<a href=\"${env.BUILD_URL}\">${currentBuild.fullDisplayName} is reported as ${currentBuild.currentResult}</a>")
			}
		}
	}
}
*/
