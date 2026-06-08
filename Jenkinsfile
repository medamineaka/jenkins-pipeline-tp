pipeline {
    agent any
    stages {
        stage('SonarQube Analysis') {
            steps {
                withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {
                    sh """
                        docker run --rm \
                        --network host \
                        -v \${WORKSPACE}:/usr/src \
                        -e SONAR_HOST_URL=http://localhost:9000 \
                        -e SONAR_TOKEN=\${SONAR_TOKEN} \
                        sonarsource/sonar-scanner-cli \
                        -Dsonar.projectKey=jenkins-tp \
                        -Dsonar.projectName=jenkins-tp \
                        -Dsonar.sources=/usr/src
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
