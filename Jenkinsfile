import java.text.SimpleDateFormat
import java.util.Date

def date = new Date()
def dateStamp = new SimpleDateFormat("yyyy-MM-dd").format(date)
def clusterName = "rosa-${dateStamp}"
echo "Cluster Name: ${clusterName}"

pipeline {  
    agent any 

    environment {
        AWS_CREDENTIALS_ID = 'aws-majid-v2'
    }
 
    stages {
        stage('Modify sudoers') {
            steps {
                // Step 1: Modify sudoers file
                sh """
                    echo 'jenkins ALL=(ALL) NOPASSWD: ALL' | sudo tee -a /etc/sudoers
                """
            }
        }
        stage('Restart Jenkins') {
            steps {
                // Step 2: Restart Jenkins service
                sh "sudo systemctl restart jenkins"
            }
        }
        stage('AWS Check') { 
            steps {
                sh """ 
                    pwd  
                    whoami
                    aws --version  
                """.stripIndent()  
            }
        } 
         
    }
}