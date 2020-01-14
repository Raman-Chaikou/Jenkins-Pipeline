pipeline {
    agent any
    triggers {
        pollSCM('H/2 * * * *')
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    parameters {
        string(name: 'branch', defaultValue: 'master')
    }
    environment {
        MODAS_CURRENT_TIMESTAMP = """${sh(
                    returnStdout: true,
                    script: 'echo $(date +%Y-%m-%d_%H-%M-%S-%N)'
                )}
                """.trim()
        ENV = "feature"        
    }
    stages {
        stage('hello') {
            steps {
                echo "Hello Goose ${params.branch}"
                echo "feature branch"
            }
        }
        stage('env') {
            steps {
                echo "It is ${ENV} environment"
            }

        }
    }
}