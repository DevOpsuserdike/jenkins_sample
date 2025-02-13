pipeline {
    agent any
    environment {
        Name = "Siddhesh"
           }
    stages {
        stage ("chechout stage"){
            steps {
                script{
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkinswithgithub', url: 'https://github.com/DevOpsuserdike/webapp.git']])
                    echo "checkout stage is completed"
                    echo "listing all file and folders"
                    sh 'ls'
                }
            }
        }
        stage ("build stage"){
            steps {
                echo "build stage is started"
                echo "check mvn version"
                sh 'mvn --version'
                echo "create a local artifacts"
                sh 'mvn install'
                echo "listing the atifact created"
                sh 'ls /var/lib/jenkins/workspace/pipeline_sample/webapp/target/*'
            }
        }
    }
}