pipeline {
    agent any
 //   parameters {
 //       choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
 //   }
    parameters {
            choice(name: 'CHOICE', choices: ['section1', 'section2'], description: 'Pick something')
    }
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
                echo "Choice: ${params.CHOICE}"
//                timeout(time: 30, unit: 'SECONDS') {
//                    script {
//                        def doesJavaRock = input(message: 'Please Provide Input', ok: 'Yes', 
//                            parameters: [booleanParam(defaultValue: true, 
                        //env.ENVIRONMENT = doesJavaRock.ENVIRONMENT
                        // Show the select input modal
//                        def INPUT_PARAMS = input message: 'Please Provide Parameters', ok: 'Next',
//                            parameters: [
//                                choice(name: 'ENVIRONMENT', choices: ['section1','section2'].join('\n'), description: 'Please select the Environment')   
//                            ]
                        //env = INPUT_PARAMS.ENVIRONMENT 
//                    }
//                }
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
