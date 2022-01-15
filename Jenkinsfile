pipeline {
    agent any 
    stages {
        stage('Clone the repo') {
            steps {
                echo 'clone the repo'
                sh 'rm -fr html'
                sh 'git clone https://github.com/dmccuk/html.git'
            }
        }
        stage('install app dependencies') {
            steps {
                sshagent(['DeployServer'])
                    sh '''
                    echo 'connect to remote host and install the app dependencies'
                    ssh -o StrictHostKeyChecking=no ubuntu@13.232.207.109 hostname 
                    ssh -o StrictHostKeyChecking=no ubuntu@13.232.207.109 ls
                    ssh -o StrictHostKeyChecking=no ubuntu@13.232.207.109 pwd
                    '''
            }
        }
        stage('install app2 dependencies') {
            steps {
                echo 'connect to remote host and install the app dependencies'
                sh 'ssh -o StrictHostKeyChecking=no -i ~/demo.pem ubuntu@13.232.207.109 sudo sh install_dependencies'
            }
        }
        stage('push repo to remote host') {
            steps {
                echo 'connect to remote host and pull down the latest version'
                sh 'ssh -o StrictHostKeyChecking=no -i ~/demo.pem ubuntu@13.232.207.109 sudo git -C /var/www/html pull'
            }
        }
        stage('Check website is up') {
            steps {
                echo 'Check website is up'
                sh 'curl -Is 13.232.207.109 | head -n 1'
            }
        }
    }
}
