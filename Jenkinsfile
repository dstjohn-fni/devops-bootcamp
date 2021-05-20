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
                def scannerHome = tool 'SonarQube-4.6.2';
                    withSonarQubeEnv("sonarqube-container") {
                        sh '${tool("SonarQube-4.6.2")}/bin/sonar-scanner'
                    }
               }
            }
        }
    }
}
