pipeline {
    agent any

    parameters {
        choice(name: 'BRANCH_NAME', choices: [], description: 'Branch to fetch the Jenkinsfile from')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the specified branch
                    checkout([$class: 'GitSCM', branches: [[name: "*/${params.BRANCH_NAME}"]],
                              doGenerateSubmoduleConfigurations: false,
                              extensions: [[$class: 'SparseCheckoutPaths', sparseCheckoutPaths: [[path: 'Jenkinsfile']]]],
                              userRemoteConfigs: [[url: 'https://github.com/sreeharsha-alluri/Test_Multiple_Branches.git']]])
                }
            }
        }

        stage('Load and Run Jenkinsfile') {
            steps {
                script {
                    echo "Print statement from main branch"
                }
            }
        }
    }
}
