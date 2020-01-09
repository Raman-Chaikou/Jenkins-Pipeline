pipeline {
    agent { 
        docker { 
            image 'maven:3.3.3' 
        } 
    }
    triggers {
        pollSCM('H/3 * * * *')
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