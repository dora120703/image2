pipeline {
    agent { label 'built-in' } 
    
    environment {
        ZONE = 'us-central1-a'
        IMAGE_NAME = "poc-app2-image-${BUILD_NUMBER}"
    }
    
    stages {
        stage('Cleanup') {
            steps {
                catchError {
                    bat 'ci/cleanup_images.bat'
                }
            }
        }
        stage('Apply Ansible config') {
            steps {
                dir('ansible') {
                    bat 'echo Processing secondary deployment maps inside submodule...'
                }
            }
        }
        stage('Create Image') {
            steps {
                bat 'ci/create_image.bat'
            }
        }
    }
}
