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
                ansiblePlaybook('ansible-playbook.yml') 
//                    extraVars {
//                        extraVar("image_name", "docker.io/cambridgesemantics/anzograph:latest", true)
//                        extraVar("container_name", "anzograph", true)
//                        extraVar("http", "80:8080", true)
//                        extraVar("https", "443:8443", true)
                    
                //}
            }
//            steps {
//                sh "ansible-playbook ansible-playbook.yml -t ${params.CHOICE}"
//            }
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
