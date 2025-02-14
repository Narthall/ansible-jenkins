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

        stage('Run Docker Playbook') {
            steps {
                ansiblePlaybook inventory: 'inventory.ini', playbook: 'playbook-docker.yml'
            }
        }

        stage('Run Apache Playbook') {
            steps {
                ansiblePlaybook inventory: 'inventory.ini', playbook: 'playbook-apache.yml'
            }
        }
    }
}
