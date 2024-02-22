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
                    sudo echo 'nokia'
                """
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