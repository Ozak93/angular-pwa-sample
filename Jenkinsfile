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
                sh 'cd /var/www/devenv.digiarenas.com/apps/browser/ '
                
                sh 'pm2 start "ng serve --host 0.0.0.0"'
            }
        }
    }
}