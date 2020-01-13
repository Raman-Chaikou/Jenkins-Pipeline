pipeline {
    agent any
    triggers {
        pollSCM('H/3 * * * *')
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment {
        MODAS_CURRENT_TIMESTAMP = """${sh(
                    returnStdout: true,
                    script: 'echo $(date +%Y-%m-%d_%H-%M-%S-%N)'
                )}
                """.trim()
        ENV = "dev"        
    }
    stages {
        stage('hello') {
            steps {
                echo "Hello Goose ${params.branch}"
            }
        }
        stage('env') {
            steps {
                echo "It is ${ENV} environment"
            }

        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
    }
}