pipeline {
    agent none 
    stages {
        stage('Clone') {
            agent { label 'myMAC' }
            steps {
               deleteDir()
               git credentialsId: 'github-id', url: 'https://github.com/mlgsalvador/Project_Ansible.git' 
            }
        }
        stage('Create host file') {
            agent {label 'myMAC'}
            steps {
               sh '''cat > serverb <<-\'EOF\'
[serverb]
54.227.164.74
EOF''' 
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
