node {
stage (‘Prepare environment’) {
//git branch: ‘development’, url: ‘git@bitbucket.org:example/myapp.git’
sh ‘npm install’
}
stage (‘Code analyse’) {
sh ‘echo “Run some lints”’
}
stage (‘Unit test’) {
sh ‘echo “Tests will back”’
}
stage (‘Build’) {
sh ‘npm run clean’
sh ‘npm run build’
}
stage (‘Deploy’) {
sh ‘ssh user@server rm -rf /var/www/temp_deploy/dist/’
sh ‘ssh user@server mkdir -p /var/www/temp_deploy’
sh ‘scp -r dist user@server:/var/www/temp_deploy/dist/’
sh ‘ssh user@server “rm -rf /var/www/example.com/dist/ && mv /var/www/temp_deploy/dist/ /var/www/example.com/”’
}
}
