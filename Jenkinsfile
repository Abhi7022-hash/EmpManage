
pipeline {
    agent any
 
    stages {
        stage('Clone repository') {
            steps {
                echo 'Cloning the Repository'
                
                git branch: 'main',
                url: 'https://github.com/Abhi7022-hash/EmpManage.git'
                
            }
        }
        stage("Building Application and Docker Image") {
            steps {
                echo "Building the Apllication files and Docker Image"
                sh '''
                
                docker build -t task1:v3 EmpManage
                '''
            }
        }
        stage("Remove the container") {
            steps {
                sh '''
                docker stop emsapp
                docker rm emsapp
                '''
            }
        }
        stage("Deploy the Application") {
            steps {
                echo "Deploy and Run the Application"
                sh '''
                docker run -d --name emsapp -p 8000:5000 task1:v3
                '''
            }
        }
    }
}
