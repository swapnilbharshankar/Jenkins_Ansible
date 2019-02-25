@Library('env')
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
        stage('Select ENV') {
            steps {
                timeout(time: 30, unit: 'SECONDS') {
                    script {
                        // Show the select input modal
                        def INPUT_PARAMS = input message: 'Please Provide Parameters', ok: 'Next',
                            parameters: [
                                choice(name: 'ENVIRONMENT', choices: ['section1','section2'].join('\n'), description: 'Please select the Environment'),   
                            ]
                        env.ENVIRONMENT = INPUT_PARAMS.ENVIRONMENT 
                    }
                }
            }
        }
        stage('Echo ENV') {
            steps {
                sh "Env is : ${env.ENVIRONMENT}"
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    playbook: 'ansible-playbook.yml',
                    tags: 'section1'
                )
            }
        }
    }
}
