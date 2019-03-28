

//start

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
                dir('user') {
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: '*/master']],
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [],
                        submoduleCfg: [],
                        userRemoteConfigs: [[
                            credentialsId: 'git_creds',
                            url: "https://github.com/swapnilbharshankar/Jenkins-Docker.git"
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
