pipeline {
    agent any

    stages {
        stage('Clonage du depot github') {
            steps {
                git url: 'https://github.com/dteixeiraef/asible-jenkins.git',
                    branch: 'main',
                    credentialsId: '1141550'
            }
        }
        stage('Envoie du script et des conteneurs sur la machine docker') {
            steps {
                sh '''
                ansible-playbook playbook-docker.yml playbook-apache.yml
                '''
            }
        }
    }
}