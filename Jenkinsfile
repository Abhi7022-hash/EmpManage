pipeline {
    agent any

    environment {
        IMAGE_NAME = "task1"
        IMAGE_TAG  = "v${BUILD_NUMBER}"
    }

    stages {
        stage('Cloning the Repository') {
            steps {
                echo 'Cloning the Repository'
                sh '''
                rm -rf EmpManage
                git clone https://github.com/Abhi7022-hash/EmpManage.git
                '''
            }
        }
        stage("Building Application and Docker Image") {
            steps {
                echo "Building the Application files and Docker Image"
                sh '''
                docker build -t $IMAGE_NAME:$IMAGE_TAG EmpManage
                '''
            }
        }
        stage("Removing old container") {
            steps {
                sh '''
                docker stop emsapp || true
                docker rm emsapp || true
                '''
            }
        }
        stage("Deploy the Application") {
            steps {
                echo "Deploy and Run the Application"
                sh '''
                docker run -d --name emsapp -p 8000:5000 $IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }
    }
}
