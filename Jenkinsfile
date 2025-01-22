pipeline {
    agent any
    environment {
        VENV_DIR ='venv'
    }
stages {
        stage('Cloning From Github Repo') {
            steps {
                script {
                    // Cloning From Github Repo
                    echo 'Cloning From Github Repo...'
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Project-github-token', url: 'https://github.com/Shailigajera/Airline-Customer-Satisfaction-Pridiction-.git']])
                }
            }
        }
        stage('Setup Virtual Environment') {
            steps {
                script {
                    // Setup Virtual Environment
                    echo 'Setup Virtual Environment...'
                    sh'''
                       python -m venv ${VENV_DIR}
                       . ${VENV_DIR}/bin/activate
                       pip install --upgrade pip
                       pip install -e .
                    '''
                }
            }
        }

        stage('Linting Code') {
            steps {
                script {
                    // Linting Code
                    echo 'Linting Code...'
                    sh '''
                       set -e
                       . ${VENV_DIR}/bin/activate
                       pylint application.py main.py --output=pylint-report.txt --exit-zero || echo "Pylint stage completed"
                       flake8 application.py main.py --ignore=E501,E302 --output-file=flake8-report.txt || echo "Flake8 stage completed"
                       black application.py main.py || echo "Black stage completed"
                    '''
                }
            }
        }


    }
}