pipeline {
    agent any
    environment {        
        SSHCRED         = credentials('SSH_CRED') 
    }
    stages {
        stage('Git checkout') {
            steps{
                git branch: 'main', credentialsId: 'SSH_CRED', url: 'https://github.com/Devopsnikhil4/kube.git'
                }
        }        
        stage('Moving file') {        
            steps{
                sshagent(['anisble']) {
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210'
                    sh 'scp /var/lib/jenkins/workspace/pipeline-demo/*172.31.54.210:/home/centos'
                    }    
            }
        }                                     
    }
}
