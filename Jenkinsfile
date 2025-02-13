pipeline {
    agent any
    environment {
        Name = "Siddhesh"
           }
    stages {
        stage ("chechout stage"){
            steps {
                script{
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkinswithgithub', url: 'https://github.com/DevOpsuserdike/jenkins_sample.git']])
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
//                sh 'mvn install'
                echo "listing the atifact created"
                sh 'ls /var/lib/jenkins/workspace/pipeline_sample/webapp/target/*'
            }
        }
        stage ("scanning stage"){
            steps {
                echo "scanning stage is started"
            }
        }

        stage ("repository management stage"){
            steps {
                echo "repository management stage is started"
                sh 'mvn deploy'
            }
        }
        stage ("slack notification stage"){
            steps {
                echo "Notification stage is started"
                slackSend(color: "good", message: "Notification stage is completed")
            }
        }
        
        stage ("build url slack"){
            steps {
                echo "console log details"
//                sh 'DATE=$( date '+%Y-%m-%d %R:%S.%3N' )'
                sh 'cat ${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log >> log_${BUILD_TIMESTAMP}.txt'
                slackUploadFile(channel: "#notification", filePath: "log_${BUILD_TIMESTAMP}.txt")
            }
        }
    }
}