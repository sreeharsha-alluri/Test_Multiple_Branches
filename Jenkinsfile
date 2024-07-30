pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the branch specified by the parameter
                    checkout([$class: 'GitSCM',
                        branches: [[name: "*/${BRANCH_NAME}"]],
                        userRemoteConfigs: [[url: 'https://github.com/sreeharsha-alluri/Test_Multiple_Branches.git']]
                    ])
                }
            }
        }
        stage('Echo Message') {
            steps {
                script {
                    echo "Building from the test branch"
                }
            }
        }
    }
}
