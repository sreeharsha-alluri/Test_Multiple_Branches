pipeline {
    agent any

    environment {
        PLATFORM = "${params.PLATFORM}"
        GITBRANCH = "${params.GITBRANCH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout changelog: false, poll: false, scm: [
                    $class: 'GitSCM',
                    branches: [[name: "*/${env.GITBRANCH}"]],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [[$class: 'RelativeTargetDirectory'],
                                 [$class: 'SubmoduleOption', 
                                  disableSubmodules: false, 
                                  parentCredentials: true, 
                                  recursiveSubmodules: true, 
                                  reference: '', 
                                  trackingSubmodules: false]],
                    submoduleCfg: [],
                    userRemoteConfigs: [[url: "${params.GITREPO}"]]
                ]
            }
        }

        stage('Build') {
            steps {
                echo 'Running the build process from main branch'
            }
        }
    }
}
