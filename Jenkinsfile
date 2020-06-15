
def targetMail = "jenkinsautomationuser@gmail.com"

def emailBuildStatus(targetMail) {
    emailext body: "please look into the build: ${BUILD_URL}", subject: "${currentBuild.result}: ${BUILD_TAG}", to: "${targetMail}"
}

pipeline {
	
	agent  any 

	options {
		timestamps()
	}

	// parameters {

	// }

	// environment {

	// }

	stages {
		stage('build') {
			steps{
				script {
					sh "mvn clean package"		
				}
			}
		}

		stage('test') {
			steps {
				script {
					sh 'pwd'
					sh 'ls -lrtha'
					sh 'pwd'
				}
			}
		}
		
	}
	post {
		always {
			junit "target/surefire-reports/*.xml"
			emailBuildStatus(targetMail)
			//deleteDir()
		}
	}
}
