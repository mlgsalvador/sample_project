pipeline {
    agent none 
    stages {
        stage('Clone') {
            agent { label 'myMAC' }
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/mlgsalvador/Project_Ansible.git']]])
            }
        }
    }
} 
