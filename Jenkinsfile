pipeline {
    agent any

    stages {
        stage('Initial Stage') {
          steps {
              echo "Check enviroment "
              sh "env"
              slackSend (message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.JENKINS_URL}/blue/organizations/jenkins/forward-cicd-ansible/detail/master/${env.BUILD_NUMBER})",  username: 'fabriziomaccioni', token: "xoxp-747822316753-782407268966-782519818502-4a6916c1b4540e084c51f680934a1f12", teamDomain: 'nfw-fwd', channel: 'cicd-service-deployment')
            }
        }
        stage("Gather Deployment Parameters") {
            steps {
                timeout(time: 30, unit: 'SECONDS') {
                    script {
                        env.SERVICE_NAME = input message: 'User input required', ok: 'Enter',
                            parameters: [string(defaultValue: '', description: 'Service Name', name: 'name')]
                        env.SERVICE_IP = input message: 'User input required', ok: 'Enter!',
                            parameters: [ string(defaultValue: '', description: 'Service IP', name: 'ip') ]
                        env.SERVICE_PORT = input message: 'User input required', ok: 'Enter!',
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
