pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the 'main' branch directly
                    checkout([$class: 'GitSCM',
                        branches: [[name: '*/test']],
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
