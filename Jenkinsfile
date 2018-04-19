pipeline {
    agent any
    stages {
		stage ('Prepare environment') {
            steps {
				bat ''' npm install'''
            }
        }
		stage ('Code analyse using lint') {
            steps {
				bat ''' ng lint '''
            }
        }
		stage ('e2e test') {
            steps {
				bat ''' ng e2e '''
            }
        }
		stage ('Build') {
            steps {
				bat ''' ng build --env=stage'''
            }
        }
		stage ('Deploy') {
            steps {
				bat ''' sh user@server rm -rf /var/www/temp_deploy/dist/'''
				bat ''' sh user@server mkdir -p /var/www/temp_deploy'''
				bat ''' scp -r dist user@server:/var/www/temp_deploy/dist/'''
				bat ''' sh user@server "rm -rf /var/www/example.com/dist/ && mv /var/www/temp_deploy/dist/ /var/www/example.com/"'''
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
                        emailext attachLog: true, body: 'test body', subject: 'test subject', to: 'mitesh.godhani@infostretch.com'

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
