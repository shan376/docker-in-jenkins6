pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        git branch: 'main', credentialsId: '2f96157a-bd2d-47fb-b8da-454564ee441e', url: 'https://github.com/shan376/docker-in-jenkins6.git'
      }
    }

    stage('Run Ansible') {
      steps {
        withEnv(['ANSIBLE_HOST_KEY_CHECKING=False']) {
          sh '''
            mkdir -p /var/lib/jenkins/.ssh
            chmod 700 /var/lib/jenkins/.ssh
            ansible-playbook -i "13.229.124.200," playbook.yml --private-key=/var/lib/jenkins/.ssh/id_rsa -u ubuntu
          '''
        }
      }
    }
  }
}
