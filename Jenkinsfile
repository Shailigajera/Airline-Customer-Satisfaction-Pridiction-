pipeline {
    agent any
    
    stages {
        stage('Cloning from Github Repo') {
            steps {
                script {
                    //Cloning Github Repo
                    echo 'Cloning from Github Repo...'
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'mlops-github-token', url: 'https://github.com/Shailigajera/Airline-Customer-Satisfaction-Pridiction-.git']])
                }
            }
        }

    }
}