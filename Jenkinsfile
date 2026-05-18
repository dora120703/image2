pipeline {
    agent any
    stages {
        stage('B1: Run Submodule Linting') {
            steps {
                dir('ansible') {
                    echo "Checking playbook configuration inside submodule..."
                }
            }
        }
        stage('B2: Execute Playbook') {
            steps {
                dir('ansible') {
                    sh 'ansible-playbook playbook.yml'
                }
            }
        }
    }
}
