pipeline {
    agent { 
        docker { 
            image 'maven:3.3.3' 
        } 
    }
    parameters {
        string(name: 'branch', defaultValue: 'master')
    }
    environment {
        CAT_V = 'D'
        MODAS_CURRENT_TIMESTAMP = """${sh(
                    returnStdout: true,
                    script: '$(date +%Y-%m-%d_%H-%M-%S-%N)'
                )}
                """
    }
    stages {
        stage('hello') {
            steps {
                echo "Hello Goose ${params.branch}"
            }
        }
        stage('build') {
            steps {
                sh 'printenv'
            }
        }
        stage('dev') {
            steps {
                echo "====++++deploy to dev env++++===="
                sh 'printenv'
            }
        }
        stage('qc') {
            steps {
                echo "====++++deploy to qc env++++===="
                sh 'printenv'
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