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
                sh """
                    ansible-playbook -i inventory.ini playbook-docker.yml
                """
            }
        }

        stage('Run Apache Playbook') {
            steps {
                sh """
                    ansible-playbook -i inventory.ini playbook-apache.yml
                """
            }
        }

        stage('Run Zabbix Playbook') {
            when {
                expression { return params.DEPLOY_ZABBIX }
            }
            steps {
                sh """
                    ansible-playbook -i inventory.ini playbook-zabbix.yml
                """
            }
        }
    }
}
