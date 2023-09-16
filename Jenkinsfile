node{
    stage('Git checkout'){
        git branch: 'main', url: 'https://github.com/Devopsnikhil4/kube.git'
    }
    stage('sending docker file to Ansible server over ssh'){
        
            SSHCRED = credentials('SSH_CRED') 
            sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210'
            sh 'scp /var/lib/jenkins/workspace/pipeline-demo/* centos@172.31.54.210:/home/centos'
    
    }
}