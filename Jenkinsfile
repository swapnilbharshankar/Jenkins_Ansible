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
                            url: "https://github.com/swapnilbharshankar/Jenkins_Ansible.git"
                        ]]
                    ])
                }
            }
        }
        stage('Check docker is running') {
            steps {
                echo "Hello abc"
            }
        }
    }
}