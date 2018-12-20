pipeline {
    agent none 
    stages {
        stage('Clone') {
            agent { label 'myMAC' }
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/mlgsalvador/Project_Ansible.git']]])
            }
        }
        stage('Create host file') {
            agent {label 'myMAC'}
            steps {
                sh 'vi serverb'
                writeFile file: 'Desktop/malou/sample_project/serverb', text: '''[serverb]
                                54.227.164.74'''
           }
        }
        stage('Execute Ansible') {
            agent {label 'myMAC'}
            steps {
                sh 'ansible-playbook -i serverb -u centos --become --become -user root -e "target=serverb" site.yml'
            }
        }
    }
} 
