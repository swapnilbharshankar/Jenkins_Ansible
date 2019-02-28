wordpress_image_name = 'wordpress:latest'
mysql_image_name = 'mysql:5.7'
http = '8000:80'


pipeline {
    agent any
    parameters {
            choice(name: 'CHOICE', choices: ['section1', 'section2'], description: 'Pick something')
    }
    stages{
        stage('Start Docker Service On Slave') {
            steps {
                sh "/etc/init.d/docker start"
                sh "pip uninstall idna --yes"
                sh "pip2.7 install docker-compose"
            }
        }
        stage('Choosed Option') {
            steps {
                echo "Choice: ${params.CHOICE}"
                sh "echo hello"
                echo "wordpress_image: ${wordpress_image_name}"
            }
        }
        stage('Run Ansibel Playbook') {
            steps {
                ansiblePlaybook([
                    playbook: 'ansible-playbook.yml',
                    tags: "${params.CHOICE}",
                    extraVars: [
                        wordpress_image: "${wordpress_image_name}",
                        mysql_image: "${mysql_image_name}",
                        http: "${http}",
//                        wordpress_image: "wordpress:latest",
//                        mysql_image: "mysql:5.7",
//                        http: "8000:80",
//                        extraVar [Key: 'wordpress_image', Value: 'wordpress:latest', hidden: true]
//                        extraVar [Key: 'mysql_image', Value: 'mysql:5.7', hidden: true]
//                        extraVar [Key: 'http',Value: '8000:80', hidden: true]
                    ]
                ])
//                ansiblePlaybook('ansible-playbook.yml') {
//                    extraVars {
//                        extraVar("mysql_image", "mysql:5.7", true)
//                        extraVar("wordpress_image", "wordpress:latest", true)
//                        extraVar("http", "80:8080", true)
//                    }
//                }

//                    extraVars {
//                        extraVar("image_name", "docker.io/cambridgesemantics/anzograph:latest", true)
//                        extraVar("container_name", "anzograph", true)
//                        extraVar("http", "80:8080", true)
//                        extraVar("https", "443:8443", true)
                    
                //}
            }
//            steps {
//                sh "ansible-playbook ansible-playbook.yml -t ${params.CHOICE}"
//            }
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
