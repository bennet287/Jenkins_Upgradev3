pipeline {
    agent any

    environment {
        DOTNET_VERSION = '7.0'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git 'https://github.com/bennet287/Jenkins_Upgradev3.git'
            }
        }

        stage('Restore Dependencies') {
            steps {
                script {
                    // Restore .NET dependencies
                    sh 'dotnet restore Jenkins_Upgradev3/jenkins-plugin-model/src/Pi.Web/Pi.Web.csproj'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the project
                    sh 'dotnet build Jenkins_Upgradev3/jenkins-plugin-model/src/Pi.Web/Pi.Web.csproj --configuration Release'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run unit tests (if applicable)
                    sh 'dotnet test Jenkins_Upgradev3/jenkins-plugin-model/src/Pi.Web/Pi.Web.csproj'
                }
            }
        }

        stage('Publish') {
            steps {
                script {
                    // Publish (optional step, depending on what you want to do)
                    sh 'dotnet publish Jenkins_Upgradev3/jenkins-plugin-model/src/Pi.Web/Pi.Web.csproj --configuration Release --output ./publish'
                }
            }
        }
    }

    post {
        always {
            // Clean up steps (if needed)
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
