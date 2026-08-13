pipeline {
//     agent {
//         kubernetes {
//             yaml '''
// apiVersion: v1
// kind: Pod
// spec:
//   containers:
//     - name: openfga-cli
//       image: openfga/openfga:latest
//       command:
//         - sleep
//       args:
//         - infinity
// '''
//         }
//     }
    agent any

        environment {
        OPENFGA_STORE_ID = credentials('openfga-store-id')
    }

    stages {

        stage("OpenFGA Write") {
            when {
                expression {
                    env.GIT_BRANCH == "origin/main"
                }
            }

            steps {
                
                    sh '''
                        echo "====== OpenFGA Model Write ======"

                        fga model write \
                          --api-url "http://host.docker.internal:7088" \
                          --store-id "$OPENFGA_STORE_ID" \
                          --file sample.fga

                        echo "===== OpenFGA Tuple Write ====="

                        fga tuple write \
                          --api-url "http://host.docker.internal:7088" \
                          --store-id "$OPENFGA_STORE_ID" \
                          --file tuples.json

                        echo "===== OpenFGA configuration written successfully ====="
                    '''
            }
        }
    }

    post {
        always {
            echo "======== always ========"
        }

        success {
            echo "======== pipeline executed successfully ========"
        }

        failure {
            echo "======== pipeline execution failed ========"
        }
    }
}