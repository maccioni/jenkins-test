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
                        env.SERVICE_NAME = input message: 'User input required', ok: 'Release!',
                            parameters: [choice(name: 'RELEASE_SCOPE', choices: 'patch\nminor\nmajor', description: 'Service name')]
                            parameters: [choice(name: 'RELEASE_SCOPE', choices: 'patch\nminor\nmajor', description: 'Service name')]
                        env.SERVICE_IP = input message: 'User input required', ok: 'Release!',
                            parameters: [choice(name: 'RELEASE_SCOPE', choices: 'patch\nminor\nmajor', description: 'Service name')]                    }
                    echo "${env.SERVICE_NAME}"
                    echo "${env.SERVICE_IP}"
                }
            }
        }
        stage("Use Deployment Parameters") {
         steps {
                script {
                    echo "All parameters have been set as Environment Variables"
                    echo "Service name: ${env.SERVICE_NAME}"
                    echo "Service IP: ${env.SERVICE_IP}"
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
