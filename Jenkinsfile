pipeline {
    // 1. Force the child pipeline to reuse Pipeline C's folder context
    agent none 
    
    stages {
        stage('B1: Run Submodule Linting') {
            agent any
            steps {
                dir('ansible') {
                    echo "Checking playbook configuration inside submodule..."
                }
            }
        }
        stage('B2: Execute Playbook') {
            agent any
            steps {
                dir('ansible') {
                    // 2. Wrap the command inside 'wsl' so Windows can execute the Linux binary
                    bat 'wsl ansible-playbook playbook.yml'
                }
            }
        }
    }
}
