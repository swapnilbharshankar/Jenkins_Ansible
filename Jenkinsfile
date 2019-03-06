properties([
    parameters([
        string(description: 'Branch', name: 'branch', defaultValue: 'master'),
    ])
])

pipeline {
    agent any 
    stages {
        stage ('Select Branch') {
            steps {
                dir('demo') {
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: '*/user']],
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [],
                        submoduleCfg: [],
                        userRemoteConfigs: [[
                            url: "https://github.com/swapnilbharshankar/Jenkins_Ansible.git"
                        ]]
                    ])
                }
            }
        }
        stage('Checkout Only Master Branch') {
            when { branch 'user' }
            steps {
                sh '''
                cat Jenkinsfile
                '''
            }
        }
    }
}
