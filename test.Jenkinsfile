pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'

		sh 'echo "Hello World"'
                
		sh '''
                    echo "Multiline shell steps works  ya djeddek"
                    ls -lah
                '''
            }
        }

	
    }

    post {
        always {
            emailext body: 'My Pipeline was executed on Jenkins', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'My Pipeline Job execution kho'
        }

	success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}