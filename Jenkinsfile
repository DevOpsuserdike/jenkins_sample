pipeline {
    agent { label 'linuxnode' }
    environment {
        JenkinsURL = "http://35.89.232.169:8080"
        Name = "Siddhesh"
        build__id = "${env.BUILD_ID}"
        JOB__NAME = "${env.JOB_NAME}"
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
//               sh 'mvn --version'
                echo "create a local artifacts"
//                sh 'mvn install'
                echo "listing the atifact created"
//                sh 'ls /var/lib/jenkins/workspace/pipeline_sample/webapp/target/*'
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
//                sh 'mvn deploy'
            }
        }
        stage ("slack notification stage"){
            steps {
                ech "Notification stage is started"
                slackSend(color: "good", message: "Notification stage is completed")
            }
        }
    
    }
    post { 
        always {      
            echo 'always'  
        }
        success { 
//            slackSend(color: "good", message: "${JenkinsURL}/job/$env.JOB__NAME/$env.build__id")
//              echo "${JenkinsURL}/job/$env.JOB__NAME/$env.build__id"
            build wait: false, propagate: false, job: 'pipeline_sample_succ', parameters: [string(name: 'JenkinsURL', value: "${JenkinsURL}/job/$env.JOB__NAME/$env.build__id/consoleText")], waitForStart: true
//            build wait: false, propagate: false, job: 'pipeline_sample_succ', parameters: [string(name: 'JenkinsURL', value: 'http://35.89.232.169:8080'), string(name: 'JOBNAME', value: 'pipeline_sample'), string(name: 'BUILDID', value: '1')], waitForStart: true
//            sh 'cat ${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log >> log_${BUILD_TIMESTAMP}.txt'
//            sh 'wget ${JenkinsURL}/job/${JOB_NAME}/${BUILD_ID}/consoleText >> log_${BUILD_TIMESTAMP}.txt'
//            sh 'curl -u sid:sid ${JenkinsURL}/job/${JOB_NAME}/${BUILD_ID}/consoleText >> log_${BUILD_TIMESTAMP}.txt'
//            slackUploadFile(channel: "#notification", filePath: "log_${BUILD_TIMESTAMP}.txt")
        }
        failure { 
                echo "done"
                build wait: false, propagate: false, job: 'pipeline_sample_fail', parameters: [string(name: 'JenkinsURL', value: "${JenkinsURL}/job/$env.JOB__NAME/$env.build__id/consoleText")], waitForStart: true
//            build wait: false, propagate: false, job: 'pipeline_sample_fail', parameters: [string(name: 'JenkinsURL', value: '${JenkinsURL}'), string(name: 'JOBNAME', value: '$env.JOB__NAME'), string(name: 'BUILDID', value: '$env.build__id')], waitForStart: true
//            build job: 'pipeline_sample_fail', parameters: [string(name: 'JenkinsURL', value: '${JenkinsURL}'), string(name: 'JOBNAME', value: '$env.JOB__NAME'), string(name: 'BUILDID', value: '${BUILD_ID}')]
//            sh 'cat ${JenkinsURL}/jobs/${JOB_NAME}/builds/${BUILD_ID}/consoleText >> log_${BUILD_TIMESTAMP}.txt'
//            sh 'curl -u sid:sid ${JenkinsURL}/job/${JOB_NAME}/${BUILD_ID}/consoleText >> log_${BUILD_TIMESTAMP}.txt'
//            slackUploadFile(channel: "#notification", filePath: "log_${BUILD_TIMESTAMP}.txt")  
        } 
    }

}
