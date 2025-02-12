pipeline {
    agent any
    parameters{
            choice(choices: ['Mango', 'Banana', 'Cherry'], description: 'Choose Fruit', name: 'Fruit')
    }
    environment {
        Name = "Siddhesh"
           }
    stages {
        stage ("first stage"){
            steps {
                echo "hellow world"
            }
        }
        stage ("second stage"){
            steps {

                echo "$params.Fruit"

            }
        }
        stage('parallel stage') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        sh 'sleep 5s'
                        sh 'echo "Running unit tests"'
                        // Add commands to run unit tests
                    }
                }
                stage('Integration Tests') {
                    steps {
                        sh 'echo "Running integration tests"'
                        // Add commands to run integration tests
                    }
                }
            }
        }
        stage ("last stage"){
            steps {

                echo "$env.Name"
            }
        }
        
    }
    post { 
        always { 
            echo 'always'
        }
        success { 
            echo 'success'
        }
        failure { 
            echo 'failure'
        }
    }
}