pipeline {
    agent any

    stages {
        stage('Initial Stage') {
          steps {
              echo "Check enviroment "
              sh "env"
            }
        }
        stage("Gather Deployment Parameters") {
            steps {
                timeout(time: 30, unit: 'SECONDS') {
                    script {
                        // Show the select input modal
                       def INPUT_PARAMS = input message: 'Please Provide Parameters', ok: 'Next',
                                        parameters: [
                                        choice(name: 'ENVIRONMENT', description: 'Please select the Environment'),
//                                        choice(name: 'IMAGE_TAG', ['a','b'].join('\n'), description: 'Available Docker Images')]
                        env.ENVIRONMENT = INPUT_PARAMS.ENVIRONMENT
//                        env.IMAGE_TAG = INPUT_PARAMS.IMAGE_TAG
                    }
                }
            }
        }
        stage("Use Deployment Parameters") {
         steps {
                script {
                    echo "All parameters have been set as Environment Variables"
                    echo "Selected Environment: ${env.ENVIRONMENT}"
//                    echo "Selected Tag: ${env.IMAGE_TAG}"
                    }
                }
        }
        stage('Final Stage') {
            steps {
              echo "Check enviroment "
              sh "env"
            }
        }
    }
}
