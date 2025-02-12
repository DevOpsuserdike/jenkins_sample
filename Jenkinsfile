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
        stage ("third stage"){
            steps {

                echo "$env.Name"
            }
        }
    }
}