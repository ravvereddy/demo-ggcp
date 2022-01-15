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
                echo 'connect to remote host and install the app dependencies'
                sh 'ssh -i ~/demo.pem ubuntu@13.232.207.109 sudo sh echo $hostname'
            }
        }
        stage('push repo to remote host') {
            steps {
                echo 'connect to remote host and pull down the latest version'
                sh 'ssh -i ~/demo.pem ubuntu@13.232.207.109 sudo git -C /var/www/html pull'
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
