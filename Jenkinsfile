pipeline {
    agent any
    stages{
        stage('Start Docker Service') {
            steps {
                sh "/etc/init.d/docker start"
                sh "pip uninstall idna --yes"
                sh "pip2.7 install docker-compose"
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    playbook: ansible-playbook.yml
                    inventory: /etc/ansible/hosts
                )
            }
        }
    }
}
