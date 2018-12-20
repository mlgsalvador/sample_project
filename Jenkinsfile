pipeline {
    agent { label 'ldap'} 
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
           }
        }

        stage('Execute Ansible') {
            steps {
                sh 'ansible-playbook -i serverb -u centos --become --become-user root -e "target=serverb" site.yml'
            }
        }
    }
} 
