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
        stage('SonarQube') {
            steps {
                echo 'Qubing your code'
                withSonarQubeEnv('My SonarQube Server') {
                    sh 'sonar-scanner'
                }
                //sh "/home/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonarqubescanner/bin/sonar-scanner"
            }
        }
    }
}
