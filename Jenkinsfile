pipeline {
    agent any
    tools {
        nodejs 'NodeJS_12.16.1'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building your code'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing your code'
                sh 'npm test'
            }
        }
    }
}