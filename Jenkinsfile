pipeline {
    agent any
    stages {
        stage('Git checkout') {
            steps{
                git branch: 'main', credentialsId: 'SSH_CRED', url: 'https://github.com/Devopsnikhil4/kube.git'
                }
        }        
        stage('Moving file from Jenkins to Ansible') {        
            steps{
                sshagent(['anisble']) {
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210'
                    sh 'scp /var/lib/jenkins/workspace/pipeline-demo/* centos@172.31.54.210:/home/centos'
                }    
            }
        }  
        stage('Docker Build Image'){
            steps{
                sshagent(['anisble']) {
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210 cd /home/centos'
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210 docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                }    
            }       
        }  
        stage('Docker Image tagging'){
            steps{
                sshagent(['anisble']) {
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210 cd /home/centos'
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210 docker image tag $JOB_NAME:v1.$BUILD_ID nikkum/$JOB_NAME:v1.$BUILD_ID '
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210 docker image tag $JOB_NAME:v1.$BUILD_ID nikkum/$JOB_NAME:latest'
                }    
            }       
        } 

    }
}   
