node {
stage ('Prepare environment') {

//sh 'npm install'
      bat ''' npm install'''
}
stage ('Code analyse using lint') {
bat ''' ng lint '''
}
stage ('e2e test') {
 bat ''' ng e2e '''
}
stage ('Build') {
 //bat ''' npm run clean'''
 bat ''' ng build --env=stage'''
}
            emailext attachLog: true, body: 'test body', subject: 'test subject', to: 'mitesh.godhani@infostretch.com'

stage ('Deploy') {

 bat ''' sh user@server rm -rf /var/www/temp_deploy/dist/'''
      
 bat ''' sh user@server mkdir -p /var/www/temp_deploy'''
 bat ''' scp -r dist user@server:/var/www/temp_deploy/dist/'''
 bat ''' sh user@server "rm -rf /var/www/example.com/dist/ && mv /var/www/temp_deploy/dist/ /var/www/example.com/"'''
}
      emailext attachLog: true, body: 'test body', subject: 'test subject', to: 'mitesh.godhani@infostretch.com'

}
