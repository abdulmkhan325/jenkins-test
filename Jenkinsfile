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
        // Checkout code from Git repository
        stage('AWS EC2 Check') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding', 
                    credentialsId: "${AWS_CREDENTIALS_ID}",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
                    sh 'aws ec2 describe-instances'
                }
            }
        }
        // Ansible Check
        stage('Ansible Install and Check') {
            steps {
                sh """ 
                    pwd   
                """.stripIndent()  
            }
        }
    }
}