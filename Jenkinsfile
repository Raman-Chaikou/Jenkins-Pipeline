pipeline {
    agent any
    triggers {
        pollSCM('H/3 * * * *')
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    parameters {
        string(name: 'branch', defaultValue: 'master')
        choice(name: 'ch', choices:['one', 'two'])
    }
    environment {
        MODAS_CURRENT_TIMESTAMP = """${sh(
                    returnStdout: true,
                    script: 'echo $(date +%Y-%m-%d_%H-%M-%S-%N)'
                )}
                """.trim()
    }
    stages {
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', 
                branches: [[name: "*/${params.branch}"]], 
                doGenerateSubmoduleConfigurations: false, 
                extensions: [], 
                submoduleCfg: [], 
                userRemoteConfigs: [[url: 'https://github.com/Raman-Chaikou/Jenkins-Pipeline.git']]])
            }
        }
        stage('hello') {
            steps {
                echo "Hello Goose ${params.branch}"
                echo "master branch"
            }
        }
        stage('Deploy to dev') {
            steps {
                echo "deploy to dev"
            }
        }
        stage('Deploy to QC') {
            steps {
                echo "deploy to qc"
            }
        }
    }
}