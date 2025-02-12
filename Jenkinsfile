pipeline {
    agent any
    options([parameters([choice(choices: ['Mango', 'Banana', 'Cherry'], description: 'Choose Fruit', name: 'Fruit')]), pipelineTriggers([])])
    stages {
        stage ("hellow World"){
            steps {
                echo "hellow world"
                echo "${params.Fruit}"
            }
        }
    }

}