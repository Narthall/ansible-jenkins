pipeline {
    agent any

    stages {
        stage('Clonage du depot github') {
            steps {
                git url: 'https://github.com/Narthall/ansible-jenkins.git',
                    branch: 'main',
                    credentialsId: 'deploy-ansible'
            }
        }

        stage('Installation Ansible') {
            steps {
                sh """
                    pipx install --include-deps ansible
                    pipx ensurepath
                """
            }
        }

        stage('Run Docker Playbook') {
            steps {
                sh """
                    /var/lib/jenkins/.local/pipx/venvs/ansible/bin/ansible-playbook -i inventory.ini playbook-docker.yml
                """
            }
        }

        stage('Run Apache Playbook') {
            steps {
                sh """
                    /var/lib/jenkins/.local/pipx/venvs/ansible/bin/ansible-playbook -i inventory.ini playbook-apache.yml
                """
            }
        }
    }
}
