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
           when {
               branch 'develop'
           }
           steps {
               echo "deploy to dev server"
           }
        }
        stage ('Deploy - uat'){
           when {
               branch 'staging'
           }
           steps {
               echo "deploy to uat server"
           }
        }
        stage ('Deploy - prod'){
           when {
               branch 'master'
           }
           steps {
               echo "deploy to production server"
           }
        }
    }   
}
