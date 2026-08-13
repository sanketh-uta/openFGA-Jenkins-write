pipeline{
    agent any
    stages{
        stage("Debug Branch") {
    steps {
        echo "BRANCH_NAME = ${env.BRANCH_NAME}"
        echo "GIT_BRANCH = ${env.GIT_BRANCH}"
        echo "GIT_COMMIT = ${env.GIT_COMMIT}"
        echo "CHANGE_ID = ${env.CHANGE_ID}"
        echo "CHANGE_BRANCH = ${env.CHANGE_BRANCH}"
        echo "CHANGE_TARGET = ${env.CHANGE_TARGET}"
    }
}
        stage("openFGA write"){
when {
        expression {
            env.GIT_BRANCH == "origin/main"
        }
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