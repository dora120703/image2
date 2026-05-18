pipeline {
    agent none 
    
    stages {
        stage('B1: Run Submodule Linting') {
            agent {
                node {
                    label 'built-in'
                    customWorkspace "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\poc1"
                }
            }
            steps {
                dir('ansible') {
                    echo "Checking playbook configuration inside submodule..."
                }
            }
        }
        
        stage('B2: Execute Playbook') {
            agent {
                node {
                    label 'built-in'
                    customWorkspace "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\poc1"
                }
            }
            steps {
                dir('ansible') {
                    bat 'echo Executing playbook B block on Windows agent...'
                }
            }
        }
    }
}
