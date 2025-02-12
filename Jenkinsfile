pipeline {
    agent any
    parameters{
            choice(choices: ['Mango', 'Banana', 'Cherry'], description: 'Choose Fruit', name: 'Fruit')
    }
    environment {
        Name = "Siddhesh"
           }
    stages {
        stage ("hellow World"){
            steps {
                echo "hellow world"
                echo "$params.Fruit"
                echo "$env.Fruit"
            }
        }
    }

}