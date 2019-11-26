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
        ENV = ''
    }
    stages {
        stage('hello') {
            steps {
                echo "Hello Goose ${params.branch}"
            }
        }
        stage('build') {
            steps {
                ENV = ""sh 'mvn --version'""
            }
        }
        stage('dev') {
            steps {
                echo "====++++deploy to dev env++++===="
                echo ENV
            }
        }
        stage('qc') {
            when
            steps {
                echo "====++++deploy to qc env++++===="
                echo ENV
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