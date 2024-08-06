pipeline {
    agent any
    parameters {
        string(name: 'GITBRANCH', defaultValue: 'main', description: 'Branch to build')
    }
    environment {
        GITBRANCH = "${params.GITBRANCH}"
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the branch specified by the parameter
                    checkout([$class: 'GitSCM',
                        branches: [[name: "*/${GITBRANCH}"]],
                        userRemoteConfigs: [[url: 'https://github.com/sreeharsha-alluri/Test_Multiple_Branches.git']]
                    ])
                }
            }
        }
        stage('Echo Message') {
            steps {
                script {
                    echo "Building from the main branch"
                }
            }
        }
    }
}
