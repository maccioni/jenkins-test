pipeline {
    agent any

    stages {
        stage('Initial Stage') {
          steps {
              echo "Check enviroment "
              sh "env"
              slackSend (message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.JENKINS_URL}/blue/organizations/jenkins/forward-cicd-ansible/detail/master/${env.BUILD_NUMBER})",  username: 'fabriziomaccioni', teamDomain: 'nfd-fwd', channel: 'cicd-service-deployment')
            }
        }
        stage("Gather Deployment Parameters") {
            steps {
                timeout(time: 120, unit: 'SECONDS') {
                    script {
                        env.SERVICE_NAME = input message: 'Provide Service Name', ok: 'Enter',
                            parameters: [string(defaultValue: '', description: 'Service Name', name: 'name')]
                        env.SERVICE_IP = input message: 'Provide Service IP', ok: 'Enter!',
                            parameters: [ string(defaultValue: '', description: 'Service IP', name: 'ip') ]
                        env.SERVICE_PORT = input message: 'Provide Service port', ok: 'Enter!',
                            parameters: [ string(defaultValue: '', description: 'Service port', name: 'port') ]                    }
                    echo "${env.SERVICE_NAME}"
                    echo "${env.SERVICE_IP}"
                    echo "${env.SERVICE_PORT}"
                }
            }
        }
        stage("Use Deployment Parameters") {
         steps {
                script {
                    echo "All parameters have been set as Environment Variables"
                    echo "Service name: ${env.SERVICE_NAME}"
                    echo "Service IP: ${env.SERVICE_IP}"
                    echo "Service IP: ${env.SERVICE_PORT}"
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
