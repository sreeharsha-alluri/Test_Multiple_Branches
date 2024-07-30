pipeline {
    agent any

    parameters {
        choice(name: 'BRANCH_NAME', choices: [], description: 'Branch to fetch the Jenkinsfile from')
    }

    stages {
        stage('Initialize') {
            steps {
                script {
                    // Populate the branch choices dynamically
                    def branches = sh(script: 'git ls-remote --heads https://github.com/sreeharsha-alluri/Test_Multiple_Branches.git', returnStdout: true).trim().split("\n")
                    def branchNames = branches.collect { it.split("/")[2] }
                    def uniqueBranches = branchNames.unique().sort()
                    
                    // Update the choices parameter with branch names
                    currentBuild.rawBuild.getAction(hudson.model.ParametersAction).getParameters().find { it.name == 'BRANCH_NAME' }.choices = uniqueBranches
                }
            }
        }

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
                    echo "Print from main branch"
                }
            }
        }
    }
}
