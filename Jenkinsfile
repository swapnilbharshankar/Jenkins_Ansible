pipeline {
    agent any
    stages{
        stage('Start Docker Service') {
            steps {
                sh "/etc/init.d/docker start"
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                sh 'echo "Creating Wordpress Site"'
                sh 'ansible-playbook ansible-playbook.yml'
            }
        }
    }
}
