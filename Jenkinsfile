pipeline {
    agent any

    environment {
        SSHCRED         = credentials('SSH_CRED') 
    }
    stages {
        stage('Git checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/Devopsnikhil4/kube.git'
            }
        }
        stage('sending docker file to Ansible server over ssh'){
            steps{
                sh 'ssh centos@172.31.54.210'
                sh 'scp /var/lib/jenkins/workspace/pipeline-demo/* centos@172.31.54.210:/home/centos'
            }
        }
    }
}
