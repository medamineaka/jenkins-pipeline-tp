pipeline {
    agent any
    stages {
        stage('SonarQube Analysis') {
            steps {
                withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {
                    sh """
                        docker run --rm \
                        -e SONAR_HOST_URL=http://172.17.0.1:9000 \
                        -e SONAR_TOKEN=${SONAR_TOKEN} \
                        sonarsource/sonar-scanner-cli \
                        -Dsonar.projectKey=jenkins-tp \
                        -Dsonar.projectName=jenkins-tp
                    """
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
