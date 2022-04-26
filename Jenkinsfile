pipeline {
    agent none
    stages {
        stage('Build and run C# code') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/sdk:6.0' }
            }
            environment { 
                DOTNET_CLI_HOME = '/tmp/dotnet_cli_home'
            }
            steps {
                sh 'dotnet build'
                sh 'dotnet test'
            }
        }
        stage('Build and run typescript code') {
            agent {
                docker { image 'node:17-bullseye' }
            }
            steps {
                dir("./DotnetTemplate.Web") {
                    sh 'npm ci'
                    sh 'npm run build'
                    sh 'npm run lint'
                    sh 'npm run test-with-coverage'
                }
            }
        }
    }
}