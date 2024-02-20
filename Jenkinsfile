import java.text.SimpleDateFormat
import java.util.Date

def date = new Date()
def dateStamp = new SimpleDateFormat("yyyy-MM-dd").format(date)
def clusterName = "rosa-${dateStamp}"
echo "Cluster Name: ${clusterName}"

pipeline {  
    agent any 

    stages { 
        // Checkout code from Git repository
        stage('AWS Check') {
            steps {
                sh """
                    pwd
                    aws --version
                """.stripIndent()
            }
        }
        // Ansible Check
        stage('Ansible Install and Check') {
            steps {
                sh """
                    sudo yum install ansible -y
                    ansible --version 
                """.stripIndent()  
            }
        }
    }
}