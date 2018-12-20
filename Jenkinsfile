pipeline {
    agent { label 'myMAC'} 
    stages {
        stage('Clone') {
            steps {
               deleteDir()
               git credentialsId: 'github-id', url: 'https://github.com/mlgsalvador/Project_Ansible.git' 
            }
        }

        stage('Create host file') {
            steps {
               sh '''cat > serverb <<-\'EOF\'
                    [serverb]
                    54.227.164.74
                    EOF''' 
           }
        }
    }
} 
