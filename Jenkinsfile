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
        stage('Check sudo privileage') {
            steps {
                // Step 1: Modify sudoers file
                sh """
                    sudo ls
                """
            }
        } 
        stage('Yum Upgrade') { 
            steps {
                sh """ 
                    pwd   
                    whoami
                    sudo yum upgrade -y
                    yum --version
                """.stripIndent()  
            }
        } 
        stage('Ansible Install and Check') { 
            steps {
                sh """ 
                    pwd   
                    whoami
                    sudo yum install ansible -y
                    ansible --version
                """.stripIndent()  
            }
        } 
    }
}