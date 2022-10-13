pipeline {
    agent { label '.NET6'}
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('sourcecode') {
            steps {
                git url: 'https://github.com/Prasadsgithub/dotnetcore-docs-hello-world.git', 
                branch: 'master'
            }   
        }
        stage('Build the code ') {
            steps {
                sh 'dotnet build dotnetcoresample.csproj'   
            }
        }
        stage('Archive reports') {
            steps {
                archive '/home/ubuntu/dotnetcore-docs-hello-world/bin/Debug/net6.0/publish/'
            }
        }
    }
}   