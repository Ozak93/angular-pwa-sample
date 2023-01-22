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
                sh 'cp -r dist/my-app/* /var/www/devenv.digiarenas.com/apps'
                sh 'pm2 start /var/www/devenv.digiarenas.com/apps/browser/index.html --name "my-app"'
            }
        }
    }
}