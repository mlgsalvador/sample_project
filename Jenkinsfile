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
    }
} 
