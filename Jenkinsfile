pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }

        // Add the "Deploy" stage here
	stage('Deploy') {
		steps {
			sh '''
				oc project hgsdlb-greetings
				oc start-build greeting-service --follow --wait
			'''
		}
	}
    }
}
