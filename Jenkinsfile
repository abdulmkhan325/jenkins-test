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
        // Ansible Check
        stage('AWS Check') {
            steps {
                sh """ 
                    pwd 
                    sudo su -s /bin/bash jenkins
                    whoami
                    aws --version  
                """.stripIndent()  
            }
        } 
         
    }
}