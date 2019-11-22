pipeline {
    agent { 
        docker { 
            image 'maven:3.3.3' 
        } 
    }
    parameters {
        string(name: 'branch', defaultValue: 'master')
    }
    stages {
        stage('hello') {
            steps {
                echo "Hello Goose ${params.branch}"
            }
        }
        stage('build') {
            steps {
                sh 'mvn --version'
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