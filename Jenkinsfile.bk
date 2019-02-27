pipeline {
    agent any
    parameters {
            choice(name: 'CHOICE', choices: ['section1', 'section2'], description: 'Pick something')
    }
    stages{

        stage('Start Docker Service On Slave') {
            steps {
                sh "/etc/init.d/docker start"
                sh "pip uninstall idna --yes"
                sh "pip2.7 install docker-compose"
            }
        }
        stage('Choosed Option') {
            steps {
                echo "Choice: ${params.CHOICE}"
            }
        }
        stage('Run Ansibel Playbook') {
            steps {
                sh "ansible-playbook ansible-playbook.yml -t ${params.CHOICE}"
            }
        }
//        stage('Run Ansible Playbook') {
//            steps {
//                ansiblePlaybook(
//                    playbook: 'ansible-playbook.yml',
//                    tags: '${params.CHOICE}'
//                )
//            }
//        }
    }
}
