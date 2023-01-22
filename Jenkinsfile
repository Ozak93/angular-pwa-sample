pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'whoami '
                sh 'npm install'
 
                sh 'ng build --prod'
            }
        }
        stage('Deploy') {
            steps {
                sh 'sudo cp -r dist/my-app/* /var/www/devenv.digiarenas.com/apps'
                sh 'pm2 start /var/www/devenv.digiarenas.com/apps/app/index.js --name "my-app"'
            }
        }
    }
}