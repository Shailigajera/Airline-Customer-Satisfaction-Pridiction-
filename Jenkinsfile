pipeline {
    agent any
    
    stages {
        stage('Cloning From Github Repo') {
            steps {
                script {
                    // Cloning From Github Repo
                    echo 'Cloning From Github Repo...'
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'project1-github-token', url: 'https://github.com/Shailigajera/Airline-Customer-Satisfaction-Pridiction-.git']])
                }
            }
        }
    }
}