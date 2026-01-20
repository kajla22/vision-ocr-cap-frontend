pipeline {
    agent any

    environment {
        AZURE_WEBAPP_NAME = '6517-web-app'
        AZURE_RESOURCE_GROUP = '6517-RG'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kajla22/vision-ocr-cap-frontend.git'
            }
        }

        stage('Deploy Frontend') {
            steps {
                // Copy all files to Azure Web App
                bat "az webapp up --name ${AZURE_WEBAPP_NAME} --resource-group ${AZURE_RESOURCE_GROUP} --html"
            }
        }
    }

    post {
        success {
            echo 'Frontend deployed successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
