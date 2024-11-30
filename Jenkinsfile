pipeline {
    agent any
    environment {
        CI='true'
    }
    stages {
        stage('Build') {
            steps {
                bat 'npm install'
            }
        }
        stage('Test'){
            steps {
                bat '"F:\Git\\bash.exe" -c "chmod +x ./jenkins/scripts/test.sh && ./jenkins/scripts/test.sh"'
            }
        }
    }
}
