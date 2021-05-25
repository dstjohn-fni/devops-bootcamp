pipeline {
    agent any
    tools {
        nodejs 'NodeJS_12.16.1'
        //tool name: 'SonarQube-4.6.2', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
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
            }
        }
        stage('Create Docker Image') {
            steps{
                withCredentials([usernamePassword(credentialsId: 'ECRAccess', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                    sh '''
                        echo *******************************************
                        echo $AWS_SECRET_ACCESS_KEY
                        echo $AWS_ACCESS_KEY_ID
                        echo *******************************************
                        wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
                        dpkg -i ./docker-ce-cli_18.09.9~3-0ubuntu-bionic_amd64.deb
                        apt-get update
                        apt-get install -y awscli
                        docker build -t workshopuser9:latest .
                        docker tag workshopuser9:latest workshopuser9:${BUILD_NUMBER}
                        docker tag workshopuser9:latest 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser9:latest
                        $(aws ecr get-login --region us-east-1 | sed 's/-e none//g')
                        docker push 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser9:latest
                    '''
                }
            }
        }
    }
}
