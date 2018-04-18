node {
stage ('Prepare environment') {

//sh 'npm install'
      bat ''' npm install'''
}
stage ('Code analyse') {
bat ''' 'echo "Run some lints"'''
}
stage ('Unit test') {
 bat ''' 'echo "Tests will back"'''
}
stage ('Build') {
 bat ''' 'npm run clean'''
 bat ''' 'npm run build'''
}
stage ('Deploy') {

 bat ''' 'ssh user@server rm -rf /var/www/temp_deploy/dist/'''
      
 bat ''' 'ssh user@server mkdir -p /var/www/temp_deploy'''
 bat ''' 'scp -r dist user@server:/var/www/temp_deploy/dist/'''
 bat ''' 'ssh user@server "rm -rf /var/www/example.com/dist/ && mv /var/www/temp_deploy/dist/ /var/www/example.com/"'''
}
}
