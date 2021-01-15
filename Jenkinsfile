pipeline {
    agent none
    stages {
        stage('Test JS'){
            agent {
                docker { image 'node:14-alpine'}
            }
            steps {
                sh 'echo Starting the Frontend tests'
                sh 'node --version'
                dir("DotnetTemplate.Web"){
                    sh "npm install"
                    sh "npm run build"
                    sh "npm t"
                    sh "npm run lint"
                }
            }
        }
        stage('Test C#'){
            agent {
                docker {
                    image 'mcr.microsoft.com/dotnet/core/sdk:3.1'
                    args '-e DOTNET_CLI_HOME="/tmp/DOTNET_CLI_HOME"'
                }
            }
            steps {
                sh 'echo "Starting the Backend build & test"'
                sh 'dotnet --version'
                sh 'dotnet build --configuration Release'
                sh 'dotnet test'
            }
        }
    }
}