pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/IskrenTodorov/sedo-09-2026-retake-exam-2.git'
            }
        }

        stage('Restore dependencies') {
            steps {
                sh 'dotnet restore Homies.sln'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build Homies.sln --no-restore'
            }
        }

        stage('Run unit tests') {
            steps {
                sh 'dotnet test Homies.Tests/Homies.Tests.csproj --no-build --verbosity normal'
            }
        }

        stage('Run integration tests') {
            steps {
                sh 'dotnet test Homies.IntegrationTests/Homies.IntegrationTests.csproj --no-build --verbosity normal'
            }
        }
    }
}
