pipeline {
    agent { label 'ldap'}
    environment {
            ANSIBLE_CONFIG = '${WORKSPACE}/ssh_ansible.cfg'
            ANSIBLE_FORCE_COLOR = 'true'
    }
    stages {
        stage('Clone') {
            steps {
               deleteDir()
               git credentialsId: 'github-id', url: 'https://github.com/mlgsalvador/Project_Ansible.git' 
            }
        }

        stage('Create host file') {
            steps {
            writeFile file: 'serverb', text: '''[serverb]
52.23.157.232'''
            writeFile file: 'ssh_ansible.cfg', text: '''[defaults]
host_key_checking=false
#allow_world_readable_tmpfiles=True

[ssh_connection]
control_path = /dev/shm/cp%%h-%%p-%%r'''
           }
        }

        stage('Execute Ansible') {
            steps {
                sshagent(['aws-key-id']) {
                 sh 'echo $ANSIBLE_CONFIG'
                 sh 'ansible-playbook -i serverb -u centos --become --become-user root -e "target=serverb" site.yml'
                } 
            }
        }
    }
} 
