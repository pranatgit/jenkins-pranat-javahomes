pipeline {
    agent any
    stages {
        stage ('parallel demo'){
            steps {
                parallel(
                    task1: {
                        echo "this is task-1"
                    },
                    task2: {
                        echo "this is task-2"
                    }
                )
            }
        }
    }
}
