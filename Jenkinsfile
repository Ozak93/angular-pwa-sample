pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'whoami '
                sh 'npm install'
 
                sh 'ng build'
            }
        }
        stage('Deploy') {
            steps {
            

                sh 'whoami'
                sh 'cp -r dist/my-app/* /var/www/devenv.digiarenas.com/apps'
                sh 'cd /var/www/devenv.digiarenas.com/apps/browser/ '
            
               
              
 
            }
        }
    
    }
           post { 
        success {
            withEnv(['JENKINS_NODE_COOKIE=dontkillMe']) {
                sh 'export JENKINS_NODE_COOKIE=dontKillMe'
                sh 'export JENKINS_SERVER_COOKIE=dontKillMe'
               
                 
                sh 'sudo pm2 start --watch "ng serve --host 0.0.0.0  --port 8082   " --name pwa app'
                sh 'sudo pm2 save'
              }  
        
                 
        }
    }
}