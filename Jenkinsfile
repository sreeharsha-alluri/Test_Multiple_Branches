pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }
        stage('Echo Message') {
            steps {
                script {
                    echo "Print from test branch"
                }
            }
        }
    }
}
