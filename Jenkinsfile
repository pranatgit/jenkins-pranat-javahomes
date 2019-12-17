pipeline {
    agent any
    environment {
        // adding maven to the path
        PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin"
    }
    stages {
        stage ('Maven Build'){
            steps {
               sh "mvn clean package"
            }
        }

        stage ('Deploy - dev'){
            steps {
                echo "deploy to dev environment"
            }
        }
    }   
}
