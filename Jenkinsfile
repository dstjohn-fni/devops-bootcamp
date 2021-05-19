pipeline {
    agent any
    tools {
        nodejs 'NodeJS_12.16.1'
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh 'npm install'
            }
        }
    }
}