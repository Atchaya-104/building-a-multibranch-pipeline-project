pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                bat 'npm install'
            }
        }
        stage('Test') {
            steps {
                bat '"F:\\Git\\bin\\bash.exe" -c "./jenkins/scripts/test.sh"'
            }
        }
        stage('Deliver for development') {
            when {
                branch 'development'
            }
            steps {
                bat '"F:\\Git\\bin\\bash.exe" -c "./jenkins/scripts/deliver-for-development.sh"'
                
                timeout(time: 5, unit: 'MINUTES') { // Wrap input in a timeout block
                    input message: 'Finished using the web site? (Click "Proceed" to continue)'
                }
                
                bat '"F:\\Git\\bin\\bash.exe" -c "./jenkins/scripts/kill.sh"'
            }
        }
        stage('Deploy for project') {
            when {
                branch 'project'
            }
            steps {
                bat '"F:\\Git\\bin\\bash.exe" -c "./jenkins/scripts/deploy-for-project.sh"'
                
                timeout(time: 5, unit: 'MINUTES') { // Wrap input in a timeout block
                    input message: 'Finished using the web site? (Click "Proceed" to continue)'
                }
                
                bat '"F:\\Git\\bin\\bash.exe" -c "./jenkins/scripts/kill.sh"'
            }
        }
    }
}