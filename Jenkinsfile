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
        stage('Moving file') {        
            steps{
                sshagent(['SSH_CRED']) {
                    sh 'ssh -o StrictHostKeyChecking=no centos@172.31.54.210'
                    }    
            }
        }                                     
    }
}

// Examples of scripted pipeline

// node {
//     stage('Example') {
//         if (env.BRANCH_NAME == 'master') {
//             echo 'I only execute on the master branch'
           
//         } else {
//             echo 'I execute elsewhere'
//              sh "env"
//         }
//     }
// }