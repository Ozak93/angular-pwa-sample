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
            

                sh 'whoami'
                sh 'cp -r dist/my-app/* /var/www/devenv.digiarenas.com/apps'
                sh 'cd /var/www/devenv.digiarenas.com/apps/browser/ '
            
               
              
 
            }
        }
    
    }
           post { 
        success {
            withEnv(['JENKINS_NODE_COOKIE=dontkillMe']) {
                sh 'export JENKINS_NODE_COOKIE=dontkillMe '
                sh 'pm2 start "ng serve --host 0.0.0.0  --port 8082 --name "My Angular App" "'
                sh 'pm2 save'
              }  
        
                 
        }
    }
}