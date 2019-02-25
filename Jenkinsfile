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
//                        def doesJavaRock = input(message: 'Please Provide Input', ok: 'Yes', 
                        def doesJavaRock = input(
                            message: 'Please Provide Input', ok: 'Next',
//                            parameters: [booleanParam(defaultValue: true, 
                            parameters: [ 
                                    choice($class: 'TextParameterDefinition',name: 'ENVIRONMENT', choices: ['section1','section2'].join('\n'), description: 'Please select the Environment') 
                                ]
                            )
                        //env.ENVIRONMENT = doesJavaRock.ENVIRONMENT
                        echo ("ENV:" +userInput['ENVIRONMENT'])
                        // Show the select input modal
//                        def INPUT_PARAMS = input message: 'Please Provide Parameters', ok: 'Next',
//                            parameters: [
//                                choice(name: 'ENVIRONMENT', choices: ['section1','section2'].join('\n'), description: 'Please select the Environment')   
//                            ]
                        //env = INPUT_PARAMS.ENVIRONMENT 
                    }
                }
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
