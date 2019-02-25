pipeline {
    agent any
    stages{
        stage('Start Docker Service') {
            steps {
                sh "/etc/init.d/docker start"
<<<<<<< HEAD
            }
        }
    }

    stages{
=======
                sh "pip uninstall idna --yes"
                sh "pip2.7 install docker-compose"
            }
        }
>>>>>>> 52df935c4c613547d45aff230744521c7ac5e145
        stage('Run Ansible Playbook') {
            steps {
                sh 'echo "Creating Wordpress Site"'
                sh 'ansible-playbook ansible-playbook.yml'
            }
        }
    }
}
