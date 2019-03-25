//start
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
                        branches: [[name: '*/master']],
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [],
                        submoduleCfg: [],
                        userRemoteConfigs: [[
                            credentialsId: 'git_creds',
                            url: "https://github.com/swapnilbharshankar/Jenkins_Ansible.git"
                        ]]
                    ])
                }
            }
        }
        stage('Checkout Only Master Branch') {
            when { branch 'master' }
            steps {
                sh '''
                cat Jenkinsfile
                '''
            }
        }
    }
}
