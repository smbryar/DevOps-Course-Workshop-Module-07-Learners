pipeline {
    agent none
    stages {
        stage('Build and run C# code') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/sdk:6.0' }
            }
            steps {
                echo 'Dotnet agent'
            }
        }
        stage('Build and run typescript code') {
            agent {
                docker { image 'node:17-bullseye' }
            }
            steps {
                echo 'Node agent'
            }
        }
    }
}