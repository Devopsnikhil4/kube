pipeline {
    agent {
        label any
    }
    environment {
        ENV_URL         = "pipeline.google.com" 
        SSHCRED         = credentials('SSH_CRED') 
    }   
    stages {
        stage('Stage FOUR') {
            steps {                 
                sh ''' 
                echo "This is stage Four"
                echo "Name of the URL is ${ENV_URL}"
                echo -e "\\e[31m Welcome"
                sleep 1

                ''' 
            }
        }
    }
}