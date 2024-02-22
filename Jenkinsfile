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
        stage('AWS Version Check') {
            steps {
                sh """ 
                    pwd 
                    aws --version  
                """.stripIndent()  
            }
        } 
        // Checkout code from Git repository
        stage('Ansible Install and Check') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding', 
                    credentialsId: "${AWS_CREDENTIALS_ID}",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
                    sh """  
                        sudo systemctl status jenkins
                    """.stripIndent()
                }
            }
        } 
    }
}