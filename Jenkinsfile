pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                 git 'https://github.com/Pritam-Khergade/student-ui.git'

            }
        }
         stage('docker install') {
            steps {
                 sh '''
                 sudo yum install docker -y
                 sudo systemctl start docker
                 sudo systemctl enable docker
                 '''
                }        
            }
            stage('build') {
            steps {
                sh '''
                sudo docker build -t studentui .
                '''
            }
        }
         stage('s3 bucket') {
            steps {
                echo 'Uploading Docker image to S3...'
                sh '''
                aws s3 cp /var/lib/jenkins/workspace/pipeline-name/dockerfile s3://new-jenkins1/jenkin-folder/dockerfile --region us-east-2
                '''
            }
        }

        
    } 
    

}
