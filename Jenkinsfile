pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('hello') {
            steps {
                sh 'echo Hello Goose'
            }
        }
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}