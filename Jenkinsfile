pipeline{
    agent any
    stages{
        stage("openFGA write"){
            when {
                branch "main"
            }
            steps{
                echo "=====here we will call the openFGA cli commands only in the merging happens====="
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}