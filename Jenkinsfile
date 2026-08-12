pipeline{
    agent{
        label "any"
    }
    stages{
        stage("openFGA write"){
            // when {
            //     branch "main"
            // }
            steps{
                echo "===here we will call the openFGA cli commands==="
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