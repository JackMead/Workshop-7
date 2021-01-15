pipeline {
    agent {
        docker { image 'node:14-alpine'}
    }
    stages {
        stage('Test Frontend') {
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
    }
}