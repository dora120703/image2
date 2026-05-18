pipeline {
    agent any
    
    stages {
        stage('B1: Run Playbook Linters') {
            steps {
                echo "Running syntax checking and security scans on Image 2 codebase..."
            }
        }
        stage('B2: Build VM Base Image') {
            steps {
                echo "Compiling underlying system layers for Compute Image 2..."
            }
        }
    }
}
