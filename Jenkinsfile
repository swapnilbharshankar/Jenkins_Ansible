pipeline {
    agent any
    stages{
        stage('Run Ansible Playbook') {
            steps {
                sh 'echo "Creating Wordpress Site"'
                sh 'ansible-playbook ansible-playbook.yml'     
            }
        }
    }
}
