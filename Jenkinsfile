pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', choices: ['main', 'test'], description: 'Branch to fetch the Jenkinsfile from')
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the specified branch
                script {
                    checkout([$class: 'GitSCM', branches: [[name: "*/${params.BRANCH_NAME}"]],
                              doGenerateSubmoduleConfigurations: false,
                              extensions: [],
                              submoduleCfg: [],
                              userRemoteConfigs: [[url: 'https://github.com/sreeharsha-alluri/Test_Multiple_Branches.git']]])
                }
            }
        }

        stage('Run Pipeline') {
            steps {
                script {
                    echo "Print statement from test branch"
                }
            }
        }
    }
}
