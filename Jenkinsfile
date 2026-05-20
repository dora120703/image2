pipeline {
    agent { label 'built-in' } 
    
    environment {
        ZONE = 'europe-west2-a'
        IMAGE_NAME = "${JOB_BASE_NAME}-v2-${BUILD_NUMBER}"
    }
    
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }
    
    stages {
        stage('B1: Interactive Parameters Prompt') {
            steps {
                script {
                    echo "Pipeline B detected. Requesting execution metadata..."
                    
                    // This form opens automatically right in the Jenkins UI
                    def userInput = input(
                        id: 'PipelineBInputs',
                        message: 'Provide custom parameters for Pipeline B:',
                        parameters: [
                            choice(name: 'TARGET_ENVIRONMENT', choices: ['dev', 'staging', 'production'], description: 'Select deployment env'),
                            string(name: 'RETENTION_DAYS', defaultValue: '30', description: 'Compute Image retention window')
                        ]
                    )
                    
                    // Store inputs into the active environment variables for subsequent stages to use
                    env.B_ENV = userInput.TARGET_ENVIRONMENT
                    env.B_RETENTION = userInput.RETENTION_DAYS
                }
            }
        }
        
        stage('B2: Execute Image Creation') {
            steps {
                echo "Deploying ${IMAGE_NAME} to target landscape: ${env.B_ENV}"
                echo "Setting image retention matrix to: ${env.B_RETENTION} days"
                dir('ci') {
                    bat 'create_image.bat'
                }
            }
        }
    }
}
