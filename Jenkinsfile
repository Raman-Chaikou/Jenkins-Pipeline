pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('hello') {
            steps {
                sh 'echo "Hello Goose"'
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