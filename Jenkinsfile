
import com.cwctravel.hudson.plugins.extended_choice_parameter.ExtendedChoiceParameterDefinition

def checkBox (String name, String values, String defaultValue,
              int visibleItemCnt=0, String description='', String delimiter=',') {

    // default same as number of values
    visibleItemCnt = visibleItemCnt ?: values.split(',').size()
    return new ExtendedChoiceParameterDefinition(
            name, //name,
            "PT_CHECKBOX", //type
            values, //value
            "", //projectName
            "", //propertyFile
            "", //groovyScript
            "", //groovyScriptFile
            "", //bindings
            "", //groovyClasspath
            "", //propertyKey
            defaultValue, //defaultValue
            "", //defaultPropertyFile
            "", //defaultGroovyScript
            "", //defaultGroovyScriptFile
            "", //defaultBindings
            "", //defaultGroovyClasspath
            "", //defaultPropertyKey
            "", //descriptionPropertyValue
            "", //descriptionPropertyFile
            "", //descriptionGroovyScript
            "", //descriptionGroovyScriptFile
            "", //descriptionBindings
            "", //descriptionGroovyClasspath
            "", //descriptionPropertyKey
            "", //javascriptFile
            "", //javascript
            false, //saveJSONParameterToFile
            false, //quoteValue
            visibleItemCnt, //visibleItemCount
            description, //description
            delimiter //multiSelectDelimiter
            )
}
def testParam = checkBox("opt", // name
                "opt1,opt2,opt3", // values
                "opt1", //default value
                0, //visible item cnt
                "Multi-select", // description
                )

properties(
  [parameters([testParam])]
)

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
