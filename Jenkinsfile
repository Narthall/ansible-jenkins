pipeline {
    agent any

    stages {
        stage('Clonage du depot github') {
            steps {
                git url: 'https://github.com/Narthall/ansible-jenkins.git',
                    branch: 'main',
                    credentialsId: 'github-ansible'
            }
        }
        stage('Envoi du script et des conteneurs sur la machine docker') {
            steps {
                sh '''
                ansible-playbook playbook-docker.yml playbook-apache.yml
                '''
            }
        }
    }
}
