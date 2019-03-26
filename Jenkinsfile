class dropDown
{
    def static newInst(name)
    {
        def com.cwctravel.hudson.plugins.extended_choice_parameter.ExtendedChoiceParameterDefinition test = 
          new com.cwctravel.hudson.plugins.extended_choice_parameter.ExtendedChoiceParameterDefinition(
            name,
            "PT_MULTI_SELECT",
            "A,B,C,D,E,F",  // displayed selection values
            null,//project name
            null,null,null,
            null,// bindings
            null,
            null, // propertykey
            "B", //default value
            null,null,null,
            null, //default bindings
            null,null,
            null, //descriptionPropertyValue
            null,null,null,null,null,null,
            null,// javascript file
            null, // javascript
            false, // save json param to file
            false, // quote
            5, // visible item count
            null,
            "," // separator
        )
        return test
}


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
