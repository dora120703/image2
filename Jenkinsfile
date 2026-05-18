pipeline {
    // Standard declaration allows it to take over the primary workspace folder
    agent any 
    
    stages {
        stage('B1: Verify Layout') {
            steps {
                echo "Locating submodule structure..."
                // Runs natively inside the clean workspace path where submodules are loaded
                bat 'dir ansible' 
            }
        }
        stage('B2: Run Submodule Playbook') {
            steps {
                dir('ansible') {
                    bat 'echo Executing playbook block on Windows agent...'
                }
            }
        }
    }
}
